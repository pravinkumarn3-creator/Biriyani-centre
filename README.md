<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Pravin Biryani Centre</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #fff8f0;
      color: #333;
    }
    header {
      text-align: center;
      padding: 40px 20px;
      background: #ffb347;
    }
    header h1 {
      font-size: 2.5em;
      margin: 10px 0;
      color: #fff;
    }
    header img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
    }
    .content {
      padding: 20px;
      max-width: 500px;
      margin: auto;
    }
    .content h2 {
      text-align: center;
      margin-bottom: 20px;
      color: #d35400;
    }
    label {
      display: block;
      margin: 10px 0 5px;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    .price-display {
      font-size: 1.2em;
      margin-bottom: 20px;
      color: #27ae60;
      text-align: center;
    }
    button {
      width: 100%;
      padding: 15px;
      background: #e67e22;
      border: none;
      border-radius: 10px;
      color: white;
      font-size: 1.2em;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: #d35400;
    }
    .urgency {
      text-align: center;
      margin-top: 15px;
      font-weight: bold;
      color: #c0392b;
      font-size: 1em;
    }
  </style>
</head>
<body>
  <!-- First Page -->
  <header>
    <img src="https://cdn-icons-png.flaticon.com/512/1046/1046784.png" alt="Biryani Logo" />
    <h1>Pravin Biryani Centre</h1>
    <p>Fresh, Hot & Limited Biryani Pockets Daily</p>
  </header>

  <!-- Order Form -->
  <div class="content">
    <h2>Order Your Biryani</h2>
    <form id="orderForm">
      <label for="name">Your Name:</label>
      <input type="text" id="name" required />

      <label for="phone">Phone Number:</label>
      <input type="tel" id="phone" required />

      <label for="address">Delivery Address:</label>
      <input type="text" id="address" required />

      <label for="quantity">Number of Pockets (max 10):</label>
      <input type="number" id="quantity" value="1" min="1" max="10" required />

      <div class="price-display">
        Total Price: ₹<span id="totalPrice">80</span>
      </div>

      <button type="submit">Order Now on WhatsApp</button>
    </form>

    <p class="urgency">⚡ Hurry! Only a few pockets left for today!</p>
  </div>

  <script>
    const quantityInput = document.getElementById("quantity");
    const totalPriceSpan = document.getElementById("totalPrice");
    const orderForm = document.getElementById("orderForm");

    // Auto update price
    quantityInput.addEventListener("input", () => {
      let qty = parseInt(quantityInput.value);
      if (qty > 10) {
        qty = 10;
        quantityInput.value = 10;
        alert("Maximum 10 pockets can be ordered at once!");
      }
      totalPriceSpan.textContent = qty * 80;
    });

    // Send order to WhatsApp
    orderForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const name = document.getElementById("name").value;
      const phone = document.getElementById("phone").value;
      const address = document.getElementById("address").value;
      const quantity = document.getElementById("quantity").value;
      const total = quantity * 80;

      const message = `Hello Pravin Biryani Centre! 🍲%0A
      New Order Details:%0A
      Name: ${name}%0A
      Phone: ${phone}%0A
      Address: ${address}%0A
      Quantity: ${quantity} pocket(s)%0A
      Total Price: ₹${total}`;

      window.open(`https://wa.me/916371764660?text=${message}`, "_blank");
    });
  </script>
</body>
</html>

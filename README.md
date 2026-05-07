<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Mie Ayam Bakso Order</title>

<style>
body {
  font-family: Arial;
  background: #f5f5f5;
}

.container {
  max-width: 420px;
  margin: auto;
  padding: 20px;
}

.header {
  background: #5a3825;
  color: white;
  border-radius: 20px;
  padding: 25px;
  text-align: center;
}

.card {
  background: white;
  border-radius: 18px;
  padding: 18px;
  margin-top: 20px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
}

.menu-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 12px 0;
  border-bottom: 1px solid #eee;
  padding-bottom: 10px;
}

.menu-item button {
  width: 40px;
  height: 40px;
  border-radius: 10px;
  border: none;
  background: #2d6a4f;
  color: white;
  cursor: pointer;
}

button {
  background: #2d6a4f;
  color: white;
  border: none;
  padding: 12px;
  width: 100%;
  border-radius: 12px;
  font-size: 16px;
  margin-top: 15px;
  cursor: pointer;
}

input, textarea {
  width: 100%;
  padding: 12px;
  margin-top: 10px;
  border-radius: 10px;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
</style>

</head>
<body>

<div class="container">

  <div class="header">
    <h1>Mie Ayam Bakso</h1>
    <p>Order langsung dari HP 📱</p>
  </div>

  <!-- MENU -->
  <div class="card">
    <h3>Menu</h3>

    <div class="menu-item">
      <span>Mie Ayam - 15.000</span>
      <button onclick="addItem('Mie Ayam',15000)">+</button>
    </div>

    <div class="menu-item">
      <span>Bakso - 15.000</span>
      <button onclick="addItem('Bakso',15000)">+</button>
    </div>

    <div class="menu-item">
      <span>Mie Ayam Bakso - 20.000</span>
      <button onclick="addItem('Mie Ayam Bakso',20000)">+</button>
    </div>
  </div>

  <!-- KERANJANG -->
  <div class="card">
    <h3>Keranjang</h3>
    <div id="cart"></div>
    <h4>Total: Rp <span id="total">0</span></h4>

    <button onclick="checkout()">Pesan via WhatsApp</button>
  </div>

  <!-- KRITIK SARAN -->
  <div class="card">
    <h3>Kritik & Saran</h3>
    <input id="nama" placeholder="Nama">
    <textarea id="pesan" placeholder="Tulis pesan..."></textarea>
    <button onclick="kirim()">Kirim</button>
  </div>

</div>

<script>
let cart = [];

function addItem(name, price) {
  cart.push({ name, price });
  renderCart();
}

function renderCart() {
  let cartDiv = document.getElementById("cart");
  let total = 0;

  cartDiv.innerHTML = "";

  cart.forEach(item => {
    total += item.price;
    cartDiv.innerHTML += `<div>${item.name} - Rp ${item.price}</div>`;
  });

  document.getElementById("total").innerText = total;
}

function checkout() {
  if (cart.length === 0) {
    alert("Keranjang kosong!");
    return;
  }

  let msg = "Halo saya mau pesan:%0A";

  cart.forEach(item => {
    msg += `- ${item.name} (Rp ${item.price})%0A`;
  });

  let total = cart.reduce((a,b)=>a+b.price,0);
  msg += `%0ATotal: Rp ${total}`;

  window.location.href =
  "https://wa.me/6289633311934?text=" + msg;
}

function kirim() {
  let nama = document.getElementById("nama").value;
  let pesan = document.getElementById("pesan").value;

  if (!nama || !pesan) {
    alert("Isi dulu!");
    return;
  }

  alert("Terima kasih " + nama + "!");
}
</script>

</body>
</html>

# fuzzy-octo-guacamole <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TRIZZVIVET STORE</title>
<style>
/* GLOBAL */
* {margin:0; padding:0; box-sizing:border-box; font-family:Arial, sans-serif;}
body {background:#fff; color:#111; line-height:1.5;}
a {text-decoration:none; color:inherit;}

/* NAVBAR */
.navbar {display:flex; justify-content:space-between; align-items:center; padding:20px 40px; background:white; position:sticky; top:0; border-bottom:1px solid #eee; z-index:1000;}
.logo {font-size:28px; font-weight:800; letter-spacing:2px;}
.nav-links {display:flex; gap:25px; list-style:none; font-weight:600; cursor:pointer;}
.nav-links li:hover {opacity:.7; transition:.3s;}

/* HERO */
.hero {height:80vh; display:flex; justify-content:center; align-items:center; text-align:center; color:white; background:url("https://images.unsplash.com/photo-1523381294911-8d3cead13475?q=80&w=1600") center/cover; padding:20px;}
.hero h1 {font-size:60px; margin-bottom:10px; text-shadow:2px 2px 6px #000;}
.hero p {font-size:20px; text-shadow:1px 1px 4px #000;}
.hero button {margin-top:20px; padding:14px 28px; border:none; background:#000; color:#fff; font-weight:bold; cursor:pointer; transition:.3s;}
.hero button:hover {background:#333;}

/* PRODUCTS */
.products {padding:80px 40px;}
.products h2 {text-align:center; margin-bottom:40px; font-size:32px;}
.grid {display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:40px;}
.product {text-align:center; transition:.3s;}
.product:hover {transform:scale(1.05);}
.product img {width:100%; border-radius:8px; object-fit:cover; height:300px;}
.product h3 {margin:10px 0 5px 0;}
.product p {font-weight:bold; margin-bottom:10px;}
.product button {padding:12px 20px; background:black; color:white; border:none; cursor:pointer; transition:.3s;}
.product button:hover {background:#333;}

/* DESIGNER */
.designer {padding:80px 20px; background:#f5f5f5; text-align:center;}
.designer select {padding:10px; margin:10px;}
.designer button {padding:12px 20px; background:black; color:white; border:none; cursor:pointer;}
.designer button:hover {background:#333;}
#designerPreview {margin-top:20px; display:flex; justify-content:center; gap:20px; flex-wrap:wrap;}
#designerPreview canvas {border:2px solid #111; border-radius:6px;}

/* CART */
.cart-container {position:fixed; top:80px; right:20px; background:white; border:1px solid #ccc; padding:20px; width:300px; max-height:500px; overflow-y:auto; display:none; z-index:1001; box-shadow:0 4px 12px rgba(0,0,0,0.1);}
.cart-container h3 {text-align:center; margin-bottom:10px;}
.cart-item {display:flex; justify-content:space-between; margin-bottom:8px;}

/* INFO & FOOTER */
.info {padding:80px 20px; text-align:center; font-size:18px;}
footer {padding:30px; text-align:center; border-top:1px solid #eee; font-size:16px; color:#555;}

/* MOBILE */
@media(max-width:768px) {.hero h1{font-size:40px;} .nav-links{gap:15px;font-size:14px;} .product img{height:200px;}}
</style>
</head>
<body>

<!-- NAVBAR -->
<header class="navbar">
<div class="logo">TRIZZVIVET</div>
<ul class="nav-links">
<li onclick="scrollShop()">Shop</li>
<li onclick="scrollDesigner()">Designer</li>
<li onclick="toggleCart()">Cart (<span id="cartCount">0</span>)</li>
</ul>
</header>

<!-- HERO -->
<section class="hero">
<div>
<h1>TRIZZVIVET DROP</h1>
<p>Streetwear Digital Concepts</p>
<button onclick="scrollShop()">Shop Now</button>
</div>
</section>

<!-- PRODUCTS -->
<section class="products" id="shop">
<h2>Featured Concepts</h2>
<div class="grid">
<div class="product">
<img src="https://images.unsplash.com/photo-1520975922324-1d6db4b0d9d2">
<h3>Concept Tee</h3>
<p>$20</p>
<button onclick="addToCart('Concept Tee', 20)">Add to Cart</button>
</div>
<div class="product">
<img src="https://images.unsplash.com/photo-1520974735194-7c6a1cbe0d03">
<h3>Concept Hoodie</h3>
<p>$30</p>
<button onclick="addToCart('Concept Hoodie', 30)">Add to Cart</button>
</div>
<div class="product">
<img src="https://images.unsplash.com/photo-1503342217505-b0a15ec3261c">
<h3>Concept Pants</h3>
<p>$35</p>
<button onclick="addToCart('Concept Pants', 35)">Add to Cart</button>
</div>
<div class="product">
<img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f">
<h3>Concept Cap</h3>
<p>$15</p>
<button onclick="addToCart('Concept Cap', 15)">Add to Cart</button>
</div>
<div class="product">
<img src="https://images.unsplash.com/photo-1503341455253-b2e723bb3dbb">
<h3>Concept Jacket</h3>
<p>$40</p>
<button onclick="addToCart('Concept Jacket', 40)">Add to Cart</button>
</div>
<div class="product">
<img src="https://images.unsplash.com/photo-1530845640148-3be5e5f061b6">
<h3>Concept Sneakers</h3>
<p>$50</p>
<button onclick="addToCart('Concept Sneakers', 50)">Add to Cart</button>
</div>
</div>
</section>

<!-- DESIGNER -->
<section class="designer" id="designer">
<h2>Create Your Own Concept</h2>
<select id="shirt">
<option>Black Shirt</option>
<option>White Shirt</option>
<option>Red Shirt</option>
<option>Blue Shirt</option>
</select>
<select id="pants">
<option>Black Pants</option>
<option>Grey Pants</option>
<option>Blue Jeans</option>
<option>Cargo Pants</option>
</select>
<br>
<button onclick="generateConcept()">Generate Concept</button>
<div id="designerPreview"></div>
</section>

<!-- INFO -->
<section class="info">
<h2>Digital Concept Notice</h2>
<p>All purchases are digital concepts. No physical items are shipped. Send payment via Cash App after checkout.</p>
</section>

<!-- CART -->
<div class="cart-container" id="cartContainer">
<h3>Your Cart</h3>
<div id="cartItems"></div>
<p>Total: $<span id="cartTotal">0</span></p>
<p>Send total to Cash App <strong>$simply1him</strong></p>
<button onclick="checkout()">Checkout</button>
</div>

<!-- FOOTER -->
<footer>
<p>© 2026 TRIZZVIVET</p>
</footer>

<!-- JAVASCRIPT -->
<script>
let cart = [];

function scrollShop(){document.getElementById("shop").scrollIntoView({behavior:"smooth"});}
function scrollDesigner(){document.getElementById("designer").scrollIntoView({behavior:"smooth"});}

// Generate downloadable concept screenshot
function generateConcept(){
let shirt = document.getElementById("shirt").value;
let pants = document.getElementById("pants").value;

// Create canvas
let canvas = document.createElement('canvas');
canvas.width = 400;
canvas.height = 400;
let ctx = canvas.getContext('2d');

// Background
ctx.fillStyle = '#fff';
ctx.fillRect(0,0,canvas.width,canvas.height);

// Text
ctx.fillStyle = '#111';
ctx.font = 'bold 20px Arial';
ctx.textAlign = 'center';
ctx.fillText('TRIZZVIVET Concept', canvas.width/2, 50);
ctx.fillText(shirt, canvas.width/2, 180);
ctx.fillText(pants, canvas.width/2, 220);

// Small digital watermark
ctx.font = '12px Arial';
ctx.fillStyle = '#888';
ctx.fillText('TRIZZVIVET DIGITAL CONCEPT', canvas.width/2, canvas.height-20);

let previewDiv = document.getElementById('designerPreview');
previewDiv.innerHTML = '';
previewDiv.appendChild(canvas);

// Add to cart
addToCart(shirt+' + '+pants, 25);

// Download link
let link = document.createElement('a');
link.download = 'trizzvivet_concept.png';
link.href = canvas.toDataURL();
link.textContent = 'Download Your Concept';
link.style.display = 'block';
link.style.marginTop = '10px';
link.style.color = 'black';
previewDiv.appendChild(link);
}

// CART FUNCTIONS
function addToCart(name, price){
cart.push({name:name, price:price});
updateCart();
alert(name + " added to cart");
}

function updateCart(){
document.getElementById("cartCount").innerText = cart.length;
let cartItems = document.getElementById("cartItems");
let total = 0;
cartItems.innerHTML = '';
cart.forEach((item,index)=>{
total += item.price;
cartItems.innerHTML += '<div class="cart-item">'+item.name+' - $'+item.price+' <button onclick="removeItem('+index+')">X</button></div>';
});
document.getElementById("cartTotal").innerText = total;
}

function removeItem(index){
cart.splice(index,1);
updateCart();
}

function toggleCart(){
let container = document.getElementById("cartContainer");
container.style.display = (container.style.display==='block') ? 'none' : 'block';
}

function checkout(){
if(cart.length===0){alert("Cart is empty"); return;}
let total = 0;
cart.forEach(item=>total+=item.price);
alert("Your total is $"+total+". Send this amount to Cash App $simply1him.");
window.open('https://cash.app/$simply1him','_blank');
}
</script>

</body>
</html>

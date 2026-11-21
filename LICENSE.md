
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Raja King</title>

<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #090909, #252525, #000);
  color: gold;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.box {
  width: 90%;
  max-width: 380px;
  background: #111;
  padding: 30px;
  border-radius: 20px;
  border: 1px solid gold;
  box-shadow: 0 0 25px #9b7500;
  text-align: center;
}
h1 {
  font-size: 35px;
  margin-bottom: 10px;
}
input {
  width: 100%;
  padding: 13px;
  margin: 10px 0;
  border-radius: 10px;
  border: 1px solid gold;
  background: #222;
  color: white;
  outline: none;
}
button {
  width: 100%;
  padding: 13px;
  background: gold;
  color: black;
  font-weight: bold;
  border: none;
  border-radius: 10px;
  margin-top: 12px;
  cursor: pointer;
}
button:hover {
  background: orange;
}
p { color: white; }
a {
  color: gold;
  cursor: pointer;
}
#home { display: none; }
</style>
</head>

<body>

<div class="box" id="register">
  <h1>👑 RAJA KING</h1>
  <p>Create Your Account</p>

  <input id="regName" placeholder="Enter Name">
  <input id="regUser" placeholder="Create Username">
  <input id="regPass" type="password" placeholder="Create Password">

  <button onclick="register()">REGISTER</button>
  <p>Already have an account?</p>
  <a onclick="showLogin()">Login</a>
</div>

<div class="box" id="login" style="display:none">
  <h1>👑 RAJA KING</h1>
  <p>Welcome Back</p>

  <input id="loginUser" placeholder="Username">
  <input id="loginPass" type="password" placeholder="Password">

  <button onclick="login()">LOGIN</button>
  <p>New User?</p>
  <a onclick="showRegister()">Register</a>
</div>

<div class="box" id="home">
  <h1>👑 RAJA KING 👑</h1>
  <h2 id="welcome"></h2>
  <p>Welcome to your kingdom 🔥</p>
  <button onclick="logout()">LOGOUT</button>
</div>

<script>
function register() {
  const name = document.getElementById("regName").value.trim();
  const user = document.getElementById("regUser").value.trim();
  const pass = document.getElementById("regPass").value;

  if (!name || !user || !pass) {
    alert("Fill all details!");
    return;
  }

  localStorage.setItem("rkName", name);
  localStorage.setItem("rkUser", user);
  localStorage.setItem("rkPass", pass);

  alert("Registration Successful 👑");
  showLogin();
}

function showLogin() {
  document.getElementById("register").style.display = "none";
  document.getElementById("login").style.display = "block";
}

function showRegister() {
  document.getElementById("login").style.display = "none";
  document.getElementById("register").style.display = "block";
}

function login() {
  const user = document.getElementById("loginUser").value;
  const pass = document.getElementById("loginPass").value;

  if (user === localStorage.getItem("rkUser") &&
      pass === localStorage.getItem("rkPass")) {
    document.getElementById("register").style.display = "none";
    document.getElementById("login").style.display = "none";
    document.getElementById("home").style.display = "block";
    document.getElementById("welcome").innerText =
      "Welcome " + localStorage.getItem("rkName") + " 👑";
  } else {
    alert("Wrong Username or Password ❌");
  }
}

function logout() {
  document.getElementById("home").style.display = "none";
  document.getElementById("login").style.display = "block";
}
</script>

</body>
</html>

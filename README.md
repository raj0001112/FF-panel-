<!DOCTYPE html>
<html>
<head>
    <title>Admin Login</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<div class="login-box">
    <h2>Login Panel</h2>
    <input type="text" id="user" placeholder="Username"><br><br>
    <input type="password" id="pass" placeholder="Password"><br><br>
    <button onclick="login()">Login</button>
    <p id="msg"></p>
</div>
<script src="script.js"></script>
</body>
</html>
dashboard.html

<!DOCTYPE html>
<html>
<head>
    <title>Dashboard</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<div class="sidebar">
    <h3>Admin Menu</h3>
    <a href="#">Dashboard</a>
    <a href="#">Players</a>
    <a href="#">Settings</a>
    <a href="#" onclick="logout()">Logout</a>
</div>
<div class="main">
    <h1>Welcome to Admin Panel</h1>
    <h2>Player List</h2>
    <input type="text" id="pname" placeholder="Player Name">
    <button onclick="addPlayer()">Add Player</button>
    <table border="1" id="ptable">
      <tr>
        <th>Name</th>
        <th>Weapon</th>
        <th>Action</th>
      </tr>
    </table>
</div>
<script src="script.js"></script>
</body>
</html>
style.css

body{margin:0;font-family:Arial;background:#f2f2f2;}
.login-box{width:280px;margin:120px auto;padding:18px;box-shadow:0 0 8px #888;text-align:center;border-radius:8px;background:white;}
.sidebar{width:190px;height:100vh;background:#111;position:fixed;padding-top:25px;}
.sidebar a{color:white;display:block;padding:12px;text-decoration:none;}
.sidebar a:hover{background:#333;}
.main{margin-left:210px;padding:20px;}
script.js

function login(){
    let u = document.getElementById("user").value;
    let p = document.getElementById("pass").value;
    if(u==="admin" && p==="1234"){
        window.location="dashboard.html";
    } else {
        document.getElementById("msg").innerText="Login Failed!";
    }
}
function logout(){
    window.location="login.html";
}
function addPlayer(){
    let name = document.getElementById("pname").value.trim();
    if(name==="") return;
    let table = document.getElementById("ptable");
    let row = table.insertRow(-1);
    row.innerHTML = `<td>${name}</td><td>AWM</td><td><button onclick="deleteRow(this)">Delete</button></td>`;
    document.getElementById("pname").value="";
}
function deleteRow(btn){
    let row = btn.parentElement.parentElement;
    row.remove();
}

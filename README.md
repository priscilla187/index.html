<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">   
    
<title>Login Page</title>
       
<style>
  body {
  background-color: #222222;
  color: #252424;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  display: flex;
  flex-direction: column; /* Aligns children elements vertically */
  align-items: center; /* Centers children horizontally */
  justify-content: center;
  height: 88vh;
  margin: 0;
}

.logo {
  background-image: url('Images/logo.png');
  width: 240px; /* Increase width as needed */
  height: 219px; /* Increase height as needed */
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  margin: 0 auto; /* Centers the logo horizontally */
  animation: swing 3s ease-in-out infinite; /* Applies the swinging animation */
}

@keyframes swing {
  0%, 100% {
    transform: rotate(-15deg);
  }
  50% {
    transform: rotate(15deg);
  }
}
    
.tagline {
  color: #333333; 
  text-align: center; /* To center it under the logo */
  margin-top: 25px; /* Spacing between the logo and the tagline */
  font-size: 14px;
}
    
    .tagline-xoxo {
    color: #333333; 
    margin-top: -1px;
    font-size: 14px;
    }
    
.login-box {
  padding: 20px; /* Reduced padding */
  width: 300px;
  text-align: center;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  margin-top: -50px; /* Move the box up */
}

.login-box h2 {
  font-size: 24px; /* Reduced font size */
  margin-bottom: 10px; /* Adjust space below the login header */
  color: #333333;
}

/* Add additional styles for the new sign-up text */
.sign-up-text {
  color: #333333;
  font-size: 14px; /* Adjust as needed */
  margin-top: 10px; /* Space above the sign-up text */
}

     .login-box form {
    background: #ff7ca5; /* Background color for form */
    padding: 30px;
    border-radius: 19px;
  }
    
.login-box input[type="text"],
.login-box input[type="password"] {
  width: 100%; /* This ensures the inputs fill the container */
  padding: 11px;
  margin-bottom: 8px; /* Adjust spacing between input fields */
  border: 1px solid #e1e1e1;
  border-radius: 15px;
  box-sizing: border-box;
}

.login-box input[type="submit"] {
  width: 100%; /* This ensures the button fills the container */
  padding: 11px;
  background-color: #ff427d;
  color: #ffffff;
  border: none;
  cursor: pointer;
  border-radius: 15px; /* Rounded corners for the button */
}

.login-box input[type="submit"]:hover {
  background-color: #ff3070;
}

.login-box a {
  color: #ffffff;
  text-decoration: none;
}

.login-box a:hover {
  text-decoration: underline;
}
    
 .visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    padding: 0;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    border: 0;
}
   
</style>
</head>
<body>
    
<div class="logo"></div>
<div class="login-box">
  <form id="loginForm">
    <h2>Login</h2>
    <p class="tagline">Dear Divas, Cilla Empowers Elegance, One Era at a Time -</p> <!-- Tagline under the logo -->
    <p class="tagline-xoxo"> xoxo Cilla Couture</p>
    <input type="text" id="username" placeholder="Username" required><br>
    <input type="password" id="password" placeholder="Password" required><br>
    <input type="submit" value="Sign in" class="submit-btn">
    <p><a href="#" onclick="alert('Reset password functionality not implemented.'); return false;">Forgot your password?</a></p>
    <p class="sign-up-text">Are you new to Cilla Couture? <a href="/signup">Sign up</a></p> <!-- New sign-up text -->
     
  </form>
</div>
    
<nav aria-label="Primary">
    <ul>
        <li><a href="/register.html" class="visually-hidden">Registration</a></li>
        <li><a href="/login.html" class="visually-hidden">Login</a></li>
        <li><a href="/forgot-password.html" class="visually-hidden">Forgot Password</a></li>
        <!-- The reset password link is typically sent via email and not directly accessible from the navigation -->
    </ul>
</nav>

    
<script>
document.getElementById('loginForm').onsubmit = function(event) {
  event.preventDefault();
  var email = document.getElementById('email').value;
  var password = document.getElementById('password').value;
  
  // Here you will send the email and password to the server
  fetch('/login', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({ email: email, password: password }),
  })
  .then(response => response.json())
  .then(data => {
    if (data.success) {
      // Redirect to the actual website/dashboard
      window.location.href = '/dashboard';
    } else {
      alert('Login failed!');
    }
  })
  .catch((error) => {
    console.error('Error:', error);
  });
};
</script>
    
</body>
</html>

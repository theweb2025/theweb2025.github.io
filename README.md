<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>password login</title>
    <style>
        body {
            background-color: #1b0025;
            font-family: 'Lexend', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            color: white;
        }

        .container {
            text-align: center;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            text-transform: lowercase;
        }

        input[type="password"], input[type="text"] {
            padding: 10px;
            margin-bottom: 20px;
            font-size: 1rem;
            border: 2px solid white;
            border-radius: 5px;
            color: white;
            background-color: transparent;
            outline: none;
        }

        input[type="password"]:focus, input[type="text"]:focus {
            border-color: #fff;
        }

        button {
            padding: 10px 20px;
            font-size: 1rem;
            border: 2px solid white;
            background-color: transparent;
            color: white;
            cursor: pointer;
            border-radius: 5px;
            outline: none;
        }

        button:hover {
            background-color: white;
            color: #1b0025;
        }

        .welcome-message {
            display: none;
            font-size: 2rem;
            font-weight: bold;
            color: white;
            animation: fadeInZoom 2s forwards;
        }

        @keyframes fadeInZoom {
            0% {
                opacity: 0;
                transform: scale(0.5);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }
    </style>
</head>
<body>

<div class="container">
    <h1>the web sign in</h1>
    <input type="password" id="password" placeholder="enter password">
    <br>
    <button onclick="checkPassword()">confirm</button>
    <div id="captchaContainer" style="display:none;">
        <p>solve the captcha:</p>
        <span id="captchaQuestion"></span>
        <br>
        <input type="text" id="captchaAnswer" placeholder="enter answer">
        <br>
        <button onclick="checkCaptcha()">submit captcha</button>
    </div>
    <div id="welcomeMessage" class="welcome-message">welcome!</div>
</div>

<script>
    var captchaAnswer;

    function generateCaptcha() {
        var num1 = Math.floor(Math.random() * 10);
        var num2 = Math.floor(Math.random() * 10);
        captchaAnswer = num1 + num2;
        document.getElementById("captchaQuestion").innerText = `${num1} + ${num2} = ?`;
        document.getElementById("captchaContainer").style.display = "block";
    }

    function checkPassword() {
        var password = document.getElementById("password").value;
        var correctPassword = "theweb25!";

        if (password === correctPassword) {
            document.querySelector('h1').style.display = 'none';
            document.querySelector('input[type="password"]').style.display = 'none';
            document.querySelector('button').style.display = 'none';
            generateCaptcha();
        } else {
            alert("incorrect password! please try again.");
        }
    }

    function checkCaptcha() {
        var captchaInput = document.getElementById("captchaAnswer").value;

        if (parseInt(captchaInput) === captchaAnswer) {
            document.getElementById("captchaContainer").style.display = "none";
            var welcomeMessage = document.getElementById("welcomeMessage");
            welcomeMessage.style.display = 'block';
            setTimeout(function() {
                window.location.href = "https://tinyurl.com/youareNOTgettingthelinkbucko";
            }, 2000);
        } else {
            alert("incorrect captcha! please try again.");
        }
    }
</script>

</body>
</html>

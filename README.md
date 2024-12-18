<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Guess the Number Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            background-color: #f4f4f4;
        }
        .container {
            width: 300px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        input {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin-top: 10px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            margin-top: 20px;
            border-radius: 5px;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        #message {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Guess the Number Game</h2>
        <p>Guess the number between 1 and 100:</p>
        <input type="number" id="guess" min="1" max="100" placeholder="Enter your guess" />
        <button onclick="checkGuess()">Submit Guess</button>
        <p id="message"></p>
        <p>Attempts: <span id="attempts">0</span></p>
    </div>

    <script>
        let randomNumber = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;

        function checkGuess() {
            let guess = document.getElementById("guess").value;
            let message = document.getElementById("message");
            let attemptsText = document.getElementById("attempts");

            if (!guess || guess < 1 || guess > 100) {
                message.textContent = "Please enter a valid number between 1 and 100.";
                return;
            }

            attempts++;
            attemptsText.textContent = attempts;

            if (guess < randomNumber) {
                message.textContent = "Too low! Try again.";
            } else if (guess > randomNumber) {
                message.textContent = "Too high! Try again.";
            } else {
                message.textContent = `Congratulations! You guessed the right number (${randomNumber}) in ${attempts} attempts.`;
                randomNumber = Math.floor(Math.random() * 100) + 1;  // New number after winning
                attempts = 0;
                attemptsText.textContent = attempts;
            }
        }
    </script>

</body>
</html>

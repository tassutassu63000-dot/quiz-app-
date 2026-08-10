index.html

<!DOCTYPE html>
<html>
<head>
    <title>Quiz App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="quiz">
    <h1>General Knowledge Quiz</h1>

    <h2 id="question"></h2>

    <div id="options"></div>

    <button onclick="nextQuestion()">Next</button>

    <h3 id="score"></h3>
</div>

<script src="script.js"></script>
</body>
</html>

style.css

body {
    font-family: Arial;
    background: #f2f2f2;
}

.quiz {
    width: 500px;
    margin: 80px auto;
    padding: 30px;
    background: white;
    text-align: center;
    border-radius: 10px;
}

.option {
    display: block;
    width: 100%;
    padding: 12px;
    margin: 10px 0;
    cursor: pointer;
}

button {
    padding: 10px 25px;
    cursor: pointer;
}

script.js

let questions = [
    {
        question: "What is the capital of India?",
        options: ["Mumbai", "Delhi", "Chennai", "Kolkata"],
        answer: "Delhi"
    },
    {
        question: "Which language is used for web pages?",
        options: ["HTML", "Python", "Java", "C"],
        answer: "HTML"
    },
    {
        question: "Which language adds behavior to a webpage?",
        options: ["HTML", "CSS", "JavaScript", "SQL"],
        answer: "JavaScript"
    }
];

let current = 0;
let score = 0;

function loadQuestion() {
    let q = questions[current];

    document.getElementById("question").innerText = q.question;

    let options = document.getElementById("options");
    options.innerHTML = "";

    q.options.forEach(function(option) {
        let button = document.createElement("button");

        button.innerText = option;
        button.className = "option";

        button.onclick = function() {
            if (option === q.answer) {
                score++;
            }
        };

        options.appendChild(button);
    });
}

function nextQuestion() {
    current++;

    if (current < questions.length) {
        loadQuestion();
    } else {
        document.getElementById("question").innerText = "Quiz Completed!";
        document.getElementById("options").innerHTML = "";
        document.getElementById("score").innerText =
            "Your Score: " + score + "/" + questions.length;
    }
}

loadQuestion();# quiz-app-

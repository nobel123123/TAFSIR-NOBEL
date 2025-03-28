# TAFSIR-NOBEL
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>কিতা খবর</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        h1 {
            font-size: 3em;
        }
        .animated-text {
            font-size: 3em;
            font-weight: bold;
            animation: colorChange 2s infinite alternate;
        }
        @keyframes colorChange {
            0% { color: red; }
            50% { color: blue; }
            100% { color: green; }
        }
        .content {
            margin-top: 20px;
        }
        .button {
            padding: 10px 20px;
            margin: 10px;
            cursor: pointer;
        }
        .input-box {
            padding: 5px;
        }
        .image {
            width: 300px;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <div id="page1" class="content">
        <h1>কিতা খবর</h1>
        <button class="button" onclick="showPage2()">অখটাত টিফা মারো</button>
    </div>

    <div id="page2" class="content" style="display:none;">
        <h1>তুমি ছালাখ না সিদা?</h1>
        <button class="button" onclick="showPage3('ছালাখ')">ছালাখ</button>
        <button class="button" onclick="showPage3('সিদা')">সিদা</button>
    </div>

    <div id="page3" class="content" style="display:none;">
        <h1 id="resultMessage"></h1>
        <button class="button" onclick="showPage4()">১+১ খত ?</button>
    </div>

    <div id="page4" class="content" style="display:none;">
        <h1>১+১ খত ?</h1>
        <select id="answer1" class="input-box">
            <option value="1">১</option>
            <option value="2">২</option>
            <option value="3">৩</option>
            <option value="4">৪</option>
            <option value="5">৫</option>
            <option value="6">৬</option>
            <option value="7">৭</option>
            <option value="8">৮</option>
            <option value="9">৯</option>
            <option value="10">১০</option>
        </select>
        <button class="button" onclick="checkAnswer(1)">Submit</button>
    </div>

    <div id="page5" class="content" style="display:none;">
        <h1>২+২ খত ?</h1>
        <select id="answer2" class="input-box">
            <option value="1">১</option>
            <option value="2">২</option>
            <option value="3">৩</option>
            <option value="4">৪</option>
            <option value="5">৫</option>
            <option value="6">৬</option>
            <option value="7">৭</option>
            <option value="8">৮</option>
            <option value="9">৯</option>
            <option value="10">১০</option>
        </select>
        <button class="button" onclick="checkAnswer(2)">Submit</button>
    </div>

    <div id="page6" class="content" style="display:none;">
        <h1>আইচ্ছা আমি তুমারে ফয়লা কিতা জিকাইসলাম?</h1>
        <input type="text" id="userAnswer" class="input-box" placeholder="Type your answer here">
        <button class="button" onclick="checkFinalAnswer()">Submit</button>
    </div>

    <div id="page7" class="content" style="display:none;">
        <h1 id="finalMessage"></h1>
        <img id="finalImage" class="image" src="" alt="final image">
    </div>

    <script>
        function showPage2() {
            document.getElementById('page1').style.display = 'none';
            document.getElementById('page2').style.display = 'block';
        }

        function showPage3(answer) {
            document.getElementById('page2').style.display = 'none';
            document.getElementById('page3').style.display = 'block';
            if (answer === 'ছালাখ') {
                document.getElementById('resultMessage').innerText = "অউ উত্তর দেও ছাইন";
            } else {
                document.getElementById('resultMessage').innerText = "অউ অতা নি তুমার দশা 💩";
            }
        }

        function showPage4() {
            document.getElementById('page3').style.display = 'none';
            document.getElementById('page4').style.display = 'block';
        }

        function checkAnswer(question) {
            let correctAnswer;
            if (question === 1) {
                correctAnswer = 2;
            } else if (question === 2) {
                correctAnswer = 4;
            }
            const selectedAnswer = document.getElementById(`answer${question}`).value;
            if (parseInt(selectedAnswer) === correctAnswer) {
                if (question === 1) {
                    document.getElementById('page4').style.display = 'none';
                    document.getElementById('page5').style.display = 'block';
                } else {
                    document.getElementById('page5').style.display = 'none';
                    document.getElementById('page6').style.display = 'block';
                }
            } else {
                alert('ভুল অইছে , সঠিকটা লেখ');
            }
        }

        function checkFinalAnswer() {
            const answer = document.getElementById('userAnswer').value;
            document.getElementById('page6').style.display = 'none';
            document.getElementById('page7').style.display = 'block';
            if (answer === 'তুমি ছালাখ না সিদা') {
                document.getElementById('finalMessage').innerText = "আমি ত যেলা মনো করছিলাম ইলা নায় তুমি ছালাখ  আছ 👏";
                document.getElementById('finalImage').src = "https://tenor.com/view/%C3%A7rpik-kurd%C3%AE-kurmanc%C3%AE-awesome-great-gif-10179849351394892344";
            } else {
                document.getElementById('finalMessage').innerText = "অউ অতা নি তুমার দশা 💩";
                document.getElementById('finalImage').src = "https://media2.giphy.com/media/8lgqAbycBjosxjfi9k/giphy.webp?cid=790b7611y1ket6acvxy6fhtlekk2nncpt12vrxglxu4j6i9b&ep=v1_gifs_search&rid=giphy.webp&ct=g";
                setTimeout(() => {
                    document.getElementById('page7').style.display = 'none';
                    document.body.innerHTML = '<h1>আমি তুমারে ফয়লা জিকাইসলাম তুমি ছালাখ না সিদা</h1>';
                }, 3000);
            }
        }
    </script>

</body>
</html>

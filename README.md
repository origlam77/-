# <!DOCTYPE html>
<html lang="he">
<head>
  <meta charset="UTF-8">
  <title>בוחן הכנה לקצונה עורפית</title>
  <style>
    body{
      font-family:Arial,Helvetica,sans-serif;
      direction:rtl;
      text-align:center;
      margin:40px auto;
      max-width:600px;
    }
    button{
      padding:10px 20px;
      font-size:18px;
      cursor:pointer;
    }
    #question-box{display:none;margin-top:25px;}
    #user-answer{
      width:90%;
      padding:8px;
      font-size:18px;
      direction:rtl;
      margin-top:10px;
    }
    #feedback{margin-top:12px;font-weight:bold;}
  </style>
</head>
<body>

<h1>שאלת הכנה לקצונה</h1>

<button onclick="generateQuestion()">שאל אותי שאלה</button>

<div id="question-box">
  <p id="question-text"></p>
  <input id="user-answer" type="text" placeholder="הקלד/י תשובה כאן">
  <button onclick="checkAnswer()">בדוק תשובה</button>
  <p id="feedback"></p>
</div>

<!-- קובץ השאלות -->
<script src="questions.js"></script>
<script>
let currentQuestion=null;

function generateQuestion(){
  const idx=Math.floor(Math.random()*questions.length);
  currentQuestion=questions[idx];
  document.getElementById('question-text').innerText=currentQuestion.q;
  document.getElementById('question-box').style.display='block';
  document.getElementById('feedback').innerText='';
  document.getElementById('user-answer').value='';
  document.getElementById('user-answer').focus();
}

function normalize(str){
  return str.trim().replace(/\s+/g,'').toLowerCase();
}

function checkAnswer(){
  const userAns=document.getElementById('user-answer').value;
  const ok=normalize(userAns)===normalize(currentQuestion.a);
  document.getElementById('feedback').innerText=
      ok? 'תשובה נכונה! 🎉' : `תשובה שגויה. הנכון: ${currentQuestion.a}`;
}
</script>
</body>
</html>
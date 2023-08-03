<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
    <style>
      :root {
    --color-black:black ;
     --color-white :#ffffff;
    --color-glass: rgba(255, 255, 255, 0.05);
    --color-shadow: 0 0 25px rgba(0, 0, 0, 0.5);
  }
  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: "Poppins", sans-serif;
    color: var(--color-white);
  }
  body {
    background-image: url("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTiB8giTN9Hj8QAEz4DVdCtqWbfnrKoZSo2nA&usqp=CAU");
    background-repeat: no-repeat;
    background-attachment: fixed;
    background-position: center center;
    background-size: cover;
    background-color: black;
  }
  .wrapper {
    position: absolute;
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    font-size: 16px;
  }
  .heading {
    text-align: center;
    margin-bottom: 4em;
  }
  .heading h1 {
    text-shadow: var(--color-shadow);
    font-size: 6.2em;
    font-weight: 800;
    letter-spacing: 0.15em;
  }
  .heading h3 {
    font-size: 1.6em;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    font-weight: 600;
    background-color: var(--color-glass);
    backdrop-filter: blur(12px);
    box-shadow: var(--color-shadow);
    padding: 8px 30px;
    display: inline-block;
    /* color:black; */
  }
  .countdown {
    width: 95vw;
    display: flex;
    justify-content: space-around;
    gap: 10px;
  }
  .box {
    width: 28vmin;
    height: 29vmin;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    position: relative;
    background-color:black;
  }
  span.num {
    background-color: var(--color-glass);
    backdrop-filter: blur(12px);
    height: 100%;
    width: 100%;
    display: grid;
    place-items: center;
    font-size: 4em;
    box-shadow: var(--color-shadow);
    border-radius: 0.1em;
  }
  span.num:after {
    content: "";
    position: absolute;
    background-color: var(--color-glass);
    height: 100%;
    width: 50%;
    left: 0;
  }
  span.text {
    font-size: 1em;
    background-color: var(--color-white);
    color: var(--color-black);
    display: block;
    width: 80%;
    position: relative;
    text-align: center;
    bottom: 20px;
    padding: 0.7em 0;
    font-weight: 600;
    border-radius: 0.3em;
    box-shadow: var(--color-shadow);
  }
    </style>
  </head>
  <body>
    <div class="wrapper">
      <div class="heading">
        <h3>Countdown Till</h3>
        <h1>2024</h1>
      </div>
      <div class="countdown">
        <div class="box">
          <span class="num" id="day-box">00</span>
          <span class="text">Days</span>
        </div>
        <div class="box">
          <span class="num" id="hr-box">00</span>
          <span class="text">Hours</span>
        </div>
        <div class="box">
          <span class="num" id="min-box">00</span>
          <span class="text">Minutes</span>
        </div>
        <div class="box">
          <span class="num" id="sec-box">00</span>
          <span class="text">Seconds</span>
        </div>
      </div>
    </div>
   
    <script>
    let dayBox = document.getElementById("day-box");
let hrBox = document.getElementById("hr-box");
let minBox = document.getElementById("min-box");
let secBox = document.getElementById("sec-box");
let endDate = new Date(2024, 0, 1,0, 0);
let endTime = endDate.getTime();
function countdown() {
  let todayDate = new Date();
  let todayTime = todayDate.getTime();
  let remainingTime = endTime - todayTime;
  let oneMin = 60 * 1000;
  let oneHr = 60 * oneMin;
  let oneDay = 24 * oneHr;
  let addZeroes = (num) => (num < 10 ? `0${num}` : num);
  if (endTime < todayTime) {
    clearInterval(i);
    document.querySelector(
      ".countdown"
    ).innerHTML = `<h1>Countdown Has Expired</h1>`;
  } else {
    let daysLeft = Math.floor(remainingTime / oneDay);
    let hrsLeft = Math.floor((remainingTime % oneDay) / oneHr);
    let minsLeft = Math.floor((remainingTime % oneHr) / oneMin);
    let secsLeft = Math.floor((remainingTime % oneMin) / 1000);
    dayBox.textContent = addZeroes(daysLeft);
    hrBox.textContent = addZeroes(hrsLeft);
    minBox.textContent = addZeroes(minsLeft);
    secBox.textContent = addZeroes(secsLeft);
  }
}
let i = setInterval(countdown, 1000);
countdown();</script>
  </body>
</html>

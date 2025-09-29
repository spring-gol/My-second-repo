index.html

<!DOCTYPE htm>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Weather App</title>
  <style>
    body { font-family: Arial; text-align:center; margin-top:50px; }
    input { padding:10px; }
    button { padding:10px; }
  </style>
</head>
<body>
  <h1>Weather App</h1>
  <input id="city" placeholder="Enter city">
  <button onclick="getWeather()">Check</button>
  <p id="result"></p>
  <script>
    async function getWeather() {
      const city = document.getElementById("city").value;
      const apiKey = "YOUR_API_KEY"; // از سایت OpenWeatherMap بگیر
      const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`);
      const data = await res.json();
      if (data.cod === 200) {
        document.getElementById("result").innerText = 
          `${data.name}: ${data.main.temp}°C, ${data.weather[0].description}`;
      } else {
        document.getElementById("result").innerText = "City not found!";
      }
    }
  </script>
</body>
</html>

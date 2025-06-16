# Task3
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Advanced CSS & JavaScript Project</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background-color: #f5f5f5;
    }

    h1 {
      text-align: center;
    }

    .container {
      max-width: 900px;
      margin: auto;
    }

    .section {
      background: white;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    .quiz button,
    .joke button {
      margin: 5px;
      padding: 10px 15px;
      cursor: pointer;
      border: none;
      border-radius: 5px;
      background-color: #007bff;
      color: white;
    }

    .carousel img {
      width: 100%;
      max-width: 100%;
      height: auto;
      border-radius: 8px;
    }

    @media (max-width: 768px) {
      h1 {
        font-size: 1.8rem;
      }
    }

    @media (max-width: 480px) {
      h1 {
        font-size: 1.4rem;
      }

      .quiz button,
      .joke button {
        width: 100%;
        margin-bottom: 10px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Interactive, Responsive Web Page</h1>

    <!-- Section 1: Responsive Design Demonstrated -->
    <div class="section">
      <h2>Responsive Section</h2>
      <p>This layout adjusts based on the device screen size. Resize your browser or view on different devices to test responsiveness.</p>
    </div>

    <!-- Section 2: Interactive Quiz -->
    <div class="section quiz">
      <h2>Quiz: What is the capital of France?</h2>
      <button onclick="checkAnswer('Berlin')">Berlin</button>
      <button onclick="checkAnswer('Paris')">Paris</button>
      <button onclick="checkAnswer('Madrid')">Madrid</button>
      <p id="quiz-result"></p>
    </div>

    <!-- Section 3: Image Carousel -->
    <div class="section carousel">
      <h2>Image Carousel</h2>
      <img id="carousel-img" src="https://via.placeholder.com/800x400?text=Image+1" alt="carousel" />
      <br /><br />
      <button onclick="nextImage()">Next Image</button>
    </div>

    <!-- Section 4: API Fetch -->
    <div class="section joke">
      <h2>Get a Random Joke</h2>
      <button onclick="fetchJoke()">Get Joke</button>
      <p id="joke-output"></p>
    </div>
  </div>

  <script>
    // Quiz
    function checkAnswer(answer) {
      const result = document.getElementById("quiz-result");
      result.textContent = answer === "Paris" ? "Correct!" : "Wrong, try again.";
    }

    // Carousel
    const images = [
      "https://via.placeholder.com/800x400?text=Image+1",
      "https://via.placeholder.com/800x400?text=Image+2",
      "https://via.placeholder.com/800x400?text=Image+3"
    ];
    let currentIndex = 0;
    function nextImage() {
      currentIndex = (currentIndex + 1) % images.length;
      document.getElementById("carousel-img").src = images[currentIndex];
    }

    // Fetch API
    async function fetchJoke() {
      const res = await fetch("https://official-joke-api.appspot.com/random_joke");
      const data = await res.json();
      document.getElementById("joke-output").textContent = `${data.setup} - ${data.punchline}`;
    }
  </script>
</body>
</html>

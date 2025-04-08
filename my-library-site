<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f8f8;
            text-align: center;
        }
        .container {
            width: 350px;
            margin: 50px auto;
            background: #fff;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, button {
            width: 100%;
            padding: 12px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 14px;
        }
        button {
            background-color: #6b4423;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #55321e;
        }
        .hidden {
            display: none;
        }
        .message {
            color: red;
            margin-top: 10px;
        }
        .book-list, .book-details {
            width: 60%;
            margin: 20px auto;
            background: white;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: left;
        }
        .book {
            padding: 10px;
            cursor: pointer;
            border-bottom: 1px solid #ddd;
            color: black; /* اللون الأسود */
        }
        .book:hover {
            background-color: #f1f1f1;
        }
        .book-details img {
            width: 100%;
            max-width: 300px;
            display: block;
            margin: 10px auto;
        }
        .back-button {
            margin-top: 20px;
            background-color: #333;
            color: white;
        }
        #searchPage {
            background-color: #6b4423; /* اللون البني */
            color: white; /* لتغيير النص إلى اللون الأبيض */
        }
    </style>
</head>
<body>

    <!-- Login Page -->
    <div class="container" id="loginContainer">
        <!-- Add Logo Here -->
        <div id="logo">
            <img src="https://via.placeholder.com/150?text=Logo" alt="Logo" style="width: 150px; margin-bottom: 20px;">
        </div>
        <h2>Login</h2>
        <input type="email" id="loginEmail" placeholder="Enter your email">
        <input type="password" id="loginPassword" placeholder="Enter your password">
        <button onclick="login()">Login</button>
        <p class="message" id="loginMessage"></p>
        <p>Don't have an account? <a href="#" onclick="toggleForms()">Sign up</a></p>
    </div>

    <!-- Sign Up Page -->
    <div class="container hidden" id="signupContainer">
        <h2>Sign Up</h2>
        <input type="text" id="fullName" placeholder="Enter your Full Name">
        <input type="email" id="signupEmail" placeholder="Enter your email">
        <input type="password" id="signupPassword" placeholder="Enter your password">
        <input type="password" id="confirmPassword" placeholder="Confirm your password">
        <button onclick="signup()">Sign Up</button>
        <p class="message" id="signupMessage"></p>
        <p>Already have an account? <a href="#" onclick="toggleForms()">Login</a></p>
    </div>

    <!-- Search Page -->
    <div class="container hidden" id="searchPage">
        <h2>Search for books</h2>
        <input type="text" id="searchBox" placeholder="Enter book title..." onkeyup="filterBooks()">
        <div class="book-list" id="bookList">
            <div class="book" onclick="openBook('Tarikh Altabarii')">📖 Tarikh Altabarii</div>
            <div class="book" onclick="openBook('Aljamal Fi Alnahw')">📖 Aljamal Fi Alnahw</div>
            <div class="book" onclick="openBook('Muqaddimah of Ibn Khaldun')">📖 Muqaddimah of Ibn Khaldun</div>
        </div>
    </div>

    <!-- Book Details Page -->
    <div class="book-details hidden" id="bookDetails">
        <h2 id="bookTitle"></h2>
        <p><strong>Author:</strong> <span id="bookAuthor"></span></p>
        <p><strong>Category:</strong> <span id="bookCategory"></span></p>
        <img id="bookImage" src="" alt="Book Cover">
        <p id="bookContent"></p>
        <button onclick="addToFavorites()">Add to Favorites</button>
        <br><br>
        <label for="rating">Rate this book:</label>
        <select id="rating">
            <option value="1">⭐</option>
            <option value="2">⭐⭐</option>
            <option value="3">⭐⭐⭐</option>
            <option value="4">⭐⭐⭐⭐</option>
            <option value="5">⭐⭐⭐⭐⭐</option>
        </select>
        <button onclick="saveRating()">Submit Rating</button>
        <p id="savedRating"></p>
        <br>
        <button class="back-button" onclick="goBack()">Go Back</button>
    </div>

    <script>
        const books = {
            "Tarikh Altabarii": {
                title: "Tarikh Altabarii",
                author: "Ibn Jarir al-Tabari",
                category: "History",
                content: "A comprehensive history of the world, focusing on the early Islamic period, detailing the rise of the caliphates, major historical events, and key figures from the 7th century onwards. This work remains one of the most important sources of early Islamic history.",
                image: "https://via.placeholder.com/300?text=Tarikh+Altabarii"
            },
            "Aljamal Fi Alnahw": {
                title: "Aljamal Fi Alnahw",
                author: "Ibn Malik",
                category: "Grammar",
                content: "A key Arabic grammar book that outlines the rules of syntax and morphology. This text, written in poetic form, is widely used to teach Arabic grammar and is an essential resource for students of the language. The book discusses various grammatical rules, including noun declensions, verb conjugations, and sentence structure.",
                image: "https://via.placeholder.com/300?text=Aljamal+Fi+Alnahw"
            },
            "Muqaddimah of Ibn Khaldun": {
                title: "Muqaddimah of Ibn Khaldun",
                author: "Ibn Khaldun",
                category: "Sociology",
                content: "A foundational work on the philosophy of history and sociology. Ibn Khaldun explores the dynamics of human civilization, the rise and fall of dynasties, and the nature of social cohesion. His ideas on economics, culture, and politics have had a lasting influence on modern social science.",
                image: "https://via.placeholder.com/300?text=Muqaddimah+of+Ibn+Khaldun"
            }
        };

        function toggleForms() {
            document.getElementById('loginContainer').classList.toggle('hidden');
            document.getElementById('signupContainer').classList.toggle('hidden');
        }

        function login() {
            const email = document.getElementById("loginEmail").value;
            const password = document.getElementById("loginPassword").value;
            const loginMessage = document.getElementById("loginMessage");

            const storedEmail = localStorage.getItem("email");
            const storedPassword = localStorage.getItem("password");

            if (email === storedEmail && password === storedPassword) {
                loginMessage.textContent = "";
                document.getElementById("loginContainer").classList.add("hidden");
                document.getElementById("searchPage").classList.remove("hidden");
            } else {
                loginMessage.textContent = "Invalid email or password!";
            }
        }

        function signup() {
            const fullName = document.getElementById("fullName").value;
            const email = document.getElementById("signupEmail").value;
            const password = document.getElementById("signupPassword").value;
            const confirmPassword = document.getElementById("confirmPassword").value;
            const signupMessage = document.getElementById("signupMessage");

            if (!fullName || !email || !password || !confirmPassword) {
                signupMessage.textContent = "All fields are required!";
                return;
            }

            if (password !== confirmPassword) {
                signupMessage.textContent = "Passwords do not match!";
                return;
            }

            localStorage.setItem("email", email);
            localStorage.setItem("password", password);

            alert("Account created successfully! Redirecting to login...");
            toggleForms();
        }

        function openBook(bookName) {
            const book = books[bookName];
            document.getElementById("bookTitle").textContent = book.title;
            document.getElementById("bookAuthor").textContent = book.author;
            document.getElementById("bookCategory").textContent = book.category;
            document.getElementById("bookContent").textContent = book.content;
            document.getElementById("bookImage").src = book.image;
            
            document.getElementById("searchPage").classList.add("hidden");
            document.getElementById("bookDetails").classList.remove("hidden");
        }

        function goBack() {
            document.getElementById("bookDetails").classList.add("hidden");
            document.getElementById("searchPage").classList.remove("hidden");
        }

        function addToFavorites() {
            alert("Added to Favorites!");
        }

        function saveRating() {
            alert("Rating saved!");
        }
    </script>

</body>
</html>

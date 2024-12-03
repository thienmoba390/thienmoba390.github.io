<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quản Lý Thời Gian & Quay Số Ngẫu Nhiên</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: url('https://4kwallpapers.com/images/walls/thumbs_3t/19857.jpg');
            background-size: cover;
            background-position: center;
            color: white;
        }

        header {
            text-align: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
        }

        h1 {
            margin: 0;
        }

        main {
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 10px;
            max-width: 600px;
            margin: 20px auto;
        }

        form {
            display: flex;
            flex-direction: column;
        }

        label {
            margin-bottom: 5px;
        }

        input[type="text"], input[type="time"], input[type="password"], button {
            padding: 10px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
        }

        button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        footer {
            text-align: center;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            position: relative;
            bottom: 0;
            width: 100%;
        }

        .random-number {
            margin-top: 20px;
            font-size: 24px;
            color: #ffeb3b; /* Màu vàng để nổi bật */
            font-weight: bold;
        }

        #clock {
            position: fixed;
            top: 10px;
            left: 10px;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            color: white;
            border-radius: 5px;
        }

        .github-link {
            text-align: center;
            margin-top: 20px;
            font-size: 16px;
        }

        .github-link a {
            color: #ffeb3b;
            text-decoration: none;
        }

        .github-link a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <header>
        <h1>Quản Lý Thời Gian</h1>
    </header>
    <div id="clock">00:00:00</div>
    <main>
        <h2>Đăng Nhập</h2>
        <form id="login-form">
            <label for="username">Tên Đăng Nhập:</label>
            <input type="text" id="username" placeholder="Nhập tên đăng nhập" required>
            
            <label for="password">Mật Khẩu:</label>
            <input type="password" id="password" placeholder="Nhập mật khẩu" required>
            
            <button type="submit">Đăng Nhập</button>
        </form>
        <h2>Nghe Nhạc</h2>
        <iframe width="100%" height="315" src="https://audiotruyenfull.com/wp-content/uploads/2023/07/NhacNen2.mp3" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    
        <form id="time-management-form">
            <label for="task">Nhiệm Vụ:</label>
            <input type="text" id="task" placeholder="Nhập nhiệm vụ của bạn" required>
            
            <label for="time">Thời Gian:</label>
            <input type="time" id="time" required>
            
            <button type="submit">Thêm Nhiệm Vụ</button>
        </form>
        
        <h2>Danh Sách Nhiệm Vụ</h2>
        <ul id="task-list">
            <!-- Danh sách nhiệm vụ sẽ được thêm vào đây -->
        </ ul>

        <h2>Quay Số Ngẫu Nhiên</h2>
        <button id="generate-button">Quay Số</button>
        <div id="random-number" class="random-number">Số ngẫu nhiên sẽ hiển thị ở đây</div>
    </main>
    <footer>
        <p>Bản quyền © 2024 Quản Lý Thời Gian Của Thiện</p>
    </footer>
    
    <script>
        // Đồng hồ thời gian thực
        function updateClock() {
            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            document.getElementById('clock').textContent = `${hours}:${minutes}:${seconds}`;
        }
        setInterval(updateClock, 1000);
        updateClock(); // Gọi hàm ngay lập tức để hiển thị thời gian ban đầu

        // Xử lý thêm nhiệm vụ
        const taskForm = document.getElementById('time-management-form');
        const taskList = document.getElementById('task-list');

        taskForm.addEventListener('submit', function(event) {
            event.preventDefault();
            const taskInput = document.getElementById('task');
            const timeInput = document.getElementById('time');
            const listItem = document.createElement('li');
            listItem.textContent = `${taskInput.value} - ${timeInput.value}`;
            taskList.appendChild(listItem);
            taskInput.value = '';
            timeInput.value = '';
        });

        // Quay số ngẫu nhiên
        const generateButton = document.getElementById('generate-button');
        const randomNumberDisplay = document.getElementById('random-number');

        generateButton.addEventListener('click', function() {
            const randomNumber = Math.floor(Math.random() * 9999) + 1;
            randomNumberDisplay.textContent = `Số ngẫu nhiên: ${randomNumber}`;
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="da">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>renenso cloud </title>
  <style>
    /* Farvevariabler */
    :root {
      --bg-color: #000;
      --neon-turquoise: #40E0D0;
      --neon-blue: #0D47A1;
      --text-color: #e0e0e0;
      --card-bg: #1a1a1a;
      --input-bg: #333;
    }
    
    /* Global reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--bg-color);
      color: var(--text-color);
      line-height: 1.6;
    }
    
    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 1rem;
    }
    
    /* Header med gradient og neon-effekt */
    header {
      background: linear-gradient(45deg, var(--neon-turquoise), var(--neon-blue));
      padding: 2rem 1rem;
      text-align: center;
      border-bottom: 3px solid var(--neon-turquoise);
    }
    
    header h1 {
      font-size: 2.5rem;
      text-transform: uppercase;
      text-shadow: 0 0 10px var(--neon-turquoise);
      margin-bottom: 0.5rem;
    }
    
    header p {
      font-size: 1.2rem;
      text-shadow: 0 0 5px var(--neon-blue);
    }
    
    /* Navigation */
    nav {
      background-color: var(--bg-color);
      border-top: 1px solid #444;
      border-bottom: 1px solid #444;
      margin: 1rem 0;
    }
    
    nav ul {
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }
    
    nav ul li {
      margin: 0.5rem;
    }
    
    nav ul li a {
      color: var(--text-color);
      padding: 0.8rem 1.2rem;
      text-decoration: none;
      position: relative;
      transition: 0.3s;
    }
    
    nav ul li a::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 0;
      height: 2px;
      background: var(--neon-turquoise);
      transition: width 0.3s;
    }
    
    nav ul li a:hover {
      transform: translateY(-3px);
      color: var(--neon-turquoise);
    }
    
    nav ul li a:hover::after {
      width: 100%;
    }
    
    main {
      padding: 1rem 0;
    }
    
    section {
      margin-bottom: 2rem;
      display: none;
      animation: fadeIn 0.5s;
    }
    
    section.active {
      display: block;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    
    h2, h3, h4 {
      margin-bottom: 1rem;
      text-shadow: 0 0 5px var(--neon-turquoise);
    }
    
    /* Opslagskort med glødende effekt */
    .post {
      background-color: var(--card-bg);
      padding: 1.5rem;
      margin: 1rem 0;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(64, 224, 208, 0.5);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
      position: relative;
      cursor: pointer;
    }
    
    .post:hover {
      transform: translateY(-4px);
      box-shadow: 0 0 20px rgba(64, 224, 208, 0.8);
    }
    
    .post h2 {
      color: var(--neon-turquoise);
    }
    
    .post p {
      margin-bottom: 0.5rem;
    }
    
    .post img, .post video {
      max-width: 100%;
      border-radius: 5px;
      margin-top: 0.5rem;
    }
    
    .post .post-actions {
      position: absolute;
      top: 10px;
      right: 10px;
    }
    
    .post .post-actions button {
      background: var(--neon-turquoise);
      border: none;
      color: var(--bg-color);
      padding: 0.3rem 0.6rem;
      margin-left: 5px;
      cursor: pointer;
      font-size: 0.8rem;
      border-radius: 3px;
    }
    
    /* Formularer */
    form {
      background-color: var(--card-bg);
      padding: 1.5rem;
      border-radius: 8px;
      box-shadow: 0 0 8px rgba(64, 224, 208, 0.5);
      margin-bottom: 1rem;
    }
    
    form input[type="text"],
    form input[type="password"],
    form textarea {
      width: 100%;
      padding: 0.75rem;
      margin-bottom: 1rem;
      border: 1px solid #444;
      border-radius: 4px;
      background-color: var(--input-bg);
      color: var(--text-color);
    }
    
    form input[type="file"] {
      margin-bottom: 1rem;
    }
    
    form button {
      background: var(--neon-turquoise);
      color: var(--bg-color);
      border: none;
      padding: 0.8rem 1.4rem;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1rem;
      transition: background 0.3s;
    }
    
    form button:hover {
      background: var(--neon-blue);
    }
    
    /* Upload forhåndsvisning og Cloud Files */
    #upload-preview,
    #cloud-files-list {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }
    
    #upload-preview img,
    #upload-preview video,
    #cloud-files-list img,
    #cloud-files-list video {
      max-width: 200px;
      border: 1px solid #444;
      border-radius: 4px;
    }
    
    #cloud-files-list .file-item {
      position: relative;
      border: 1px solid #444;
      border-radius: 4px;
      padding: 5px;
      background-color: var(--card-bg);
      transition: transform 0.3s;
    }
    
    #cloud-files-list .file-item:hover {
      transform: translateY(-3px);
    }
    
    #cloud-files-list .file-item button {
      position: absolute;
      top: 5px;
      right: 5px;
      background: rgb(245, 17, 17);
      border: none;
      color: #fff;
      padding: 0.2rem 0.4rem;
      font-size: 0.7rem;
      border-radius: 3px;
      cursor: pointer;
    }
    
    #cloud-files-list .file-item .info-btn,
    #cloud-files-list .file-item .download-btn {
      position: absolute;
      bottom: 5px;
      right: 5px;
      background: var(--neon-turquoise);
      border: none;
      color: var(--bg-color);
      padding: 0.2rem 0.4rem;
      font-size: 0.7rem;
      border-radius: 3px;
      cursor: pointer;
      margin-left: 3px;
    }
    
    /* Modal til fildetaljer og opslag */
    .modal {
      display: none; 
      position: fixed; 
      z-index: 1000;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0,0,0,0.8);
    }
    
    .modal-content {
      background-color: var(--card-bg);
      margin: 10% auto;
      padding: 20px;
      border: 1px solid var(--neon-turquoise);
      width: 80%;
      max-width: 500px;
      color: var(--text-color);
      border-radius: 8px;
      text-align: center;
      position: relative;
    }
    
    .modal-content .close {
      color: var(--text-color);
      position: absolute;
      top: 10px;
      right: 15px;
      font-size: 28px;
      font-weight: bold;
      cursor: pointer;
    }
    
    /* Auth meddelelses styling */
    .auth-message {
      color: rgb(255, 17, 17);
      margin-bottom: 1rem;
    }
    
    footer {
      background-color: var(--bg-color);
      text-align: center;
      padding: 1rem;
      font-size: 0.9rem;
      border-top: 1px solid #444;
      margin-top: 2rem;
    }
    
    /* Responsive design */
    @media (max-width: 600px) {
      nav ul {
        flex-direction: column;
      }
      nav ul li a {
        padding: 0.8rem;
      }
    }
  </style>
  
  <!-- Tilføjet CSS til login overlay -->
  <style>
    #login-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.95);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 10000;
    }
    #login-box {
      background: var(--card-bg);
      padding: 2rem;
      border-radius: 8px;
      text-align: center;
      box-shadow: 0 0 15px rgba(64, 224, 208, 0.8);
    }
    #login-box h2 {
      margin-bottom: 1rem;
      color: var(--neon-turquoise);
    }
    #login-box input {
      width: 100%;
      padding: 0.75rem;
      margin: 0.5rem 0;
      border: 1px solid #444;
      border-radius: 4px;
      background-color: var(--input-bg);
      color: var(--text-color);
    }
    #login-box button {
      padding: 0.75rem 1.5rem;
      border: none;
      border-radius: 4px;
      background: var(--neon-turquoise);
      color: var(--bg-color);
      font-weight: bold;
      cursor: pointer;
    }
    #login-error {
      color: rgb(255, 17, 17);
      margin-top: 1rem;
    }
  </style>
</head>
<body>
  <!-- Tilføjet login overlay -->
  <div id="login-overlay">
    <div id="login-box">
      <h2>Log ind</h2>
      <form onsubmit="checkLogin(event)">
        <input type="text" id="login_username" placeholder="Brugernavn" required>
        <input type="password" id="login_password" placeholder="Kodeord" required>
        <button type="submit">Login</button>
      </form>
      <p id="login-error"></p>
    </div>
  </div>
  
  <header>
    <div class="container">
      <h1>leas renenso cloud konto</h1>
      <p>personlige cloud </p>
    </div>
  </header>

  <nav>
    <div class="container">
      <ul>
        <!-- Fjernet knappen "Feed" og knappen "Opret Opslag" -->
        <li><a href="#" onclick="goToSection('upload-section')">Upload</a></li>
        <li><a href="#" onclick="goToSection('books-section')">Bøger</a></li>
        <li><a href="#" onclick="goToSection('cloud-files-section')">Cloud Files</a></li>
        <li><a href="#" onclick="goToSection('search-section')">Søg Opslag</a></li>
      </ul>
    </div>
  </nav>

  <main>
    <div class="container">
      <!-- Feed-sektion -->
      <section id="feed-section" class="active">
        <h2>Seneste Overførsler</h2>
        <input type="text" id="search-input" placeholder="Søg opslag..." onkeyup="searchPosts()" style="margin-bottom:1rem; padding:0.5rem; width:100%;">
        <div id="posts-container">
          <p>Ingen opslag endnu.</p>
        </div>
      </section>

      <!-- Opret Opslag -->
      <section id="post-section">
        <h2>Opret Opslag</h2>
        <form id="post-form">
          <textarea id="post-text" placeholder="Skriv dit opslag her..." rows="4"></textarea>
          <input type="file" id="post-image" accept="image/*">
          <input type="file" id="post-video" accept="video/*">
          <button type="button" onclick="createPost()">Opret Opslag</button>
        </form>
      </section>

      <!-- Upload sektion -->
      <section id="upload-section">
        <h2>Upload Billeder/Vidéoer</h2>
        <form id="upload-form">
          <input type="file" id="upload-file" accept="image/*, video/*" multiple>
          <button type="button" onclick="handleUploads()">Upload</button>
        </form>
        <div id="upload-preview"></div>
      </section>

      <!-- Bøger sektion -->
      <section id="books-section">
        <h2>Dine Bøger</h2>
        <div id="books-container">
          <p>Ingen bøger endnu. Opret en ny bog for at komme i gang!</p>
        </div>
        <hr>
        <h3>Opret Ny Bog</h3>
        <form id="book-form">
          <input type="text" id="book-title" placeholder="Bogtitel">
          <button type="button" onclick="createBook()">Opret Bog</button>
        </form>
        <div id="book-editor" style="display: none; margin-top: 20px;">
          <h3 id="current-book-title"></h3>
          <div id="book-title-edit">
            <input type="text" id="edit-book-title" placeholder="Rediger bogtitel">
            <button type="button" onclick="saveBookTitle()">Gem Titel</button>
          </div>
          <textarea id="page-content" placeholder="Skriv indhold til siden..." rows="4"></textarea>
          <div style="display: flex; align-items: center; gap: 10px; margin-bottom: 10px;">
            <label for="page-bg">Baggrundsfarve:</label>
            <input type="color" id="page-bg" value="#40E0D0">
            <label for="page-text-color">Tekstfarve:</label>
            <input type="color" id="page-text-color" value="#ffffff">
          </div>
          <button type="button" onclick="addPageToBook()">Tilføj Side</button>
          <div id="edit-page-section" style="display: none; border: 1px dashed #444; padding: 0.5rem; margin: 1rem 0;">
            <h4>Rediger Side</h4>
            <textarea id="edit-page-content" rows="4" placeholder="Rediger sideindhold..."></textarea>
            <div style="display: flex; align-items: center; gap: 10px; margin-bottom: 10px;">
              <label for="edit-page-bg">Baggrundsfarve:</label>
              <input type="color" id="edit-page-bg" value="#40E0D0">
              <label for="edit-page-text">Tekstfarve:</label>
              <input type="color" id="edit-page-text" value="#ffffff">
            </div>
            <button type="button" onclick="saveEditedPage()">Gem Ændringer</button>
            <button type="button" onclick="cancelEditPage()">Afbryd</button>
          </div>
          <div id="current-book-pages"></div>
          <button type="button" onclick="finishBook()">Færdiggør Bog</button>
        </div>
      </section>

      <!-- Cloud Files sektion med fil-søgning -->
      <section id="cloud-files-section">
        <h2>Cloud Files</h2>
        <input type="text" id="cloud-files-search" placeholder="Søg filer (fx .jpg, video)..." onkeyup="searchCloudFiles()" style="margin-bottom:1rem; padding:0.5rem; width:100%;">
        <div id="cloud-files-list">
          <p>Ingen filer uploadet endnu.</p>
        </div>
      </section>

      <!-- Søgning i opslag -->
      <section id="search-section">
        <h2>Søg</h2>
        <input type="text" id="search-input-2" placeholder="Indtast søgeord..." onkeyup="searchPosts()" style="margin-bottom:1rem; padding:0.5rem; width:100%;">
        <div id="search-results">
          <p>Ingen resultater</p>
        </div>
      </section>

      <!-- Login/Registrering -->
      <section id="login-section">
        <h2>Bruger Login / Registrering</h2>
        <div id="auth-area">
          <form id="login-form">
            <input type="text" id="login-username" placeholder="Brugernavn">
            <input type="password" id="login-password" placeholder="Adgangskode">
            <button type="button" onclick="loginUser()">Login</button>
          </form>
          <p>Har du ikke en konto? Registrer dig nedenfor:</p>
          <form id="register-form">
            <input type="text" id="register-username" placeholder="Vælg et brugernavn">
            <input type="password" id="register-password" placeholder="Vælg en adgangskode">
            <button type="button" onclick="registerUser()">Registrer</button>
          </form>
          <p class="auth-message" id="auth-message"></p>
        </div>
      </section>
    </div>
  </main>
  
  <!-- Modal til fildetaljer (bruges fortsat til filer) -->
  <div id="file-modal" class="modal">
    <div class="modal-content">
      <span class="close" onclick="closeModal('file-modal')">&times;</span>
      <div id="modal-body"></div>
    </div>
  </div>
  
  <!-- Modal til opslag (post modal) -->
  <div id="post-modal" class="modal">
    <div class="modal-content" id="post-modal-content">
      <span class="close" onclick="closeModal('post-modal')">&times;</span>
      <!-- Indhold indlæses dynamisk -->
    </div>
  </div>
  
  <footer>
    <div class="container">
      <p>© 2025 renenso cloud</p>
    </div>
  </footer>
  
  <script>
    // --- Tilføjet login script ---
    function checkLogin(e) {
      e.preventDefault();
      var username = document.getElementById("login_username").value;
      var password = document.getElementById("login_password").value;
      if (username === "leabg" && password === "vta86qtzb") {
        document.getElementById("login-overlay").style.display = "none";
      } else {
        document.getElementById("login-error").innerText = "Forkert brugernavn eller kodeord.";
      }
    }
  </script>
  <script>
    // --- Globale Variabler ---
    let posts = [];
    let books = [];
    let currentBook = null;
    let currentEditingPageId = null;
    let uploads = [];
    let users = [];
    let currentUser = null;
    
    // --- Ved sideindlæsning ---
    document.addEventListener("DOMContentLoaded", function() {
      loadPosts();
      loadBooks();
      loadUploads();
      loadUsers();
      updateAuthStatus();
      renderPosts();
      renderBooks();
      renderCloudFiles();
      showSection("feed-section");
    });
    
    // --- Navigation & sektioner ---
    function showSection(sectionId) {
      const sections = document.querySelectorAll("main section");
      sections.forEach(sec => {
        if(sec.id === sectionId) {
          sec.classList.add("active");
        } else {
          sec.classList.remove("active");
        }
      });
    }
    
    function goToSection(sectionName) {
      showSection(sectionName);
      if(sectionName === "upload-section") loadUploadsPreview();
    }
    
    // --- LocalStorage Helper-funktioner ---
    function loadPosts() {
      posts = JSON.parse(localStorage.getItem("posts")) || [];
    }
    function savePosts() {
      localStorage.setItem("posts", JSON.stringify(posts));
    }
    
    function loadBooks() {
      books = JSON.parse(localStorage.getItem("books")) || [];
    }
    function saveBooks() {
      localStorage.setItem("books", JSON.stringify(books));
    }
    
    function loadUploads() {
      uploads = JSON.parse(localStorage.getItem("uploads")) || [];
    }
    function saveUploads() {
      localStorage.setItem("uploads", JSON.stringify(uploads));
    }
    
    function loadUsers() {
      users = JSON.parse(localStorage.getItem("users")) || [];
    }
    function saveUsers() {
      localStorage.setItem("users", JSON.stringify(users));
    }
    
    // --- Opslag funktioner ---
    function createPost() {
      const text = document.getElementById("post-text").value;
      const imageInput = document.getElementById("post-image");
      const videoInput = document.getElementById("post-video");
    
      function postAndRender(imageData, videoData) {
        const author = currentUser ? currentUser.username : "Gæst";
        // Tilføj likes og kommentarer til opslaget
        const post = { 
          id: Date.now(), 
          text: text, 
          image: imageData, 
          video: videoData, 
          author: author,
          timestamp: new Date().toISOString(),
          likes: [],
          comments: []
        };
        posts.unshift(post);
        savePosts();
        document.getElementById("post-form").reset();
        renderPosts();
      }
    
      if (imageInput.files && imageInput.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const imageData = e.target.result;
          if (videoInput.files && videoInput.files[0]) {
            const videoURL = URL.createObjectURL(videoInput.files[0]);
            postAndRender(imageData, videoURL);
          } else {
            postAndRender(imageData, null);
          }
        };
        reader.readAsDataURL(imageInput.files[0]);
      } else {
        if (videoInput.files && videoInput.files[0]) {
          const videoURL = URL.createObjectURL(videoInput.files[0]);
          postAndRender(null, videoURL);
        } else {
          postAndRender(null, null);
        }
      }
    }
    
    function deletePost(postId) {
      posts = posts.filter(post => post.id !== postId);
      savePosts();
      renderPosts();
    }
    
    function editPost(postId) {
      const post = posts.find(p => p.id === postId);
      if(!post || !currentUser || currentUser.username !== post.author) return;
      const newText = prompt("Rediger din tekst:", post.text);
      if(newText !== null && newText.trim() !== "") {
        post.text = newText;
        savePosts();
        renderPosts();
        openPostModal(postId);
      }
    }
    
    function renderPosts() {
      const container = document.getElementById("posts-container");
      container.innerHTML = "";
      if (posts.length === 0) {
        container.innerHTML = "<p>Ingen opslag endnu. Vær den første til at poste!</p>";
        return;
      }
      posts.forEach(post => {
        const postElem = document.createElement("div");
        postElem.className = "post";
        const dateStr = new Date(post.timestamp).toLocaleString();
        postElem.innerHTML = `<h2>Opslag af ${post.author} - ${dateStr}</h2><p>${post.text}</p>`;
        if (post.image) {
          const img = document.createElement("img");
          img.src = post.image;
          postElem.appendChild(img);
        }
        if (post.video) {
          const video = document.createElement("video");
          video.src = post.video;
          video.controls = true;
          postElem.appendChild(video);
        }
        // Klik på opslag for at se detaljer (modal)
        postElem.onclick = () => openPostModal(post.id);
    
        // Kun postens forfatter kan slette/ændre opslaget
        if(currentUser && currentUser.username === post.author) {
          const actions = document.createElement("div");
          actions.className = "post-actions";
          const deleteBtn = document.createElement("button");
          deleteBtn.innerText = "Slet";
          deleteBtn.onclick = (e) => {
            e.stopPropagation();
            deletePost(post.id);
          };
          actions.appendChild(deleteBtn);
          const editBtn = document.createElement("button");
          editBtn.innerText = "Rediger";
          editBtn.onclick = (e) => {
            e.stopPropagation();
            editPost(post.id);
          };
          actions.appendChild(editBtn);
          postElem.appendChild(actions);
        }
        container.appendChild(postElem);
      });
    }
    
    // --- Post Modal funktioner (vis opslagdetaljer, likes, kommentarer) ---
    function openPostModal(postId) {
      const post = posts.find(p => p.id === postId);
      if(!post) return;
      const modalContent = document.getElementById("post-modal-content");
      modalContent.innerHTML = `
        <span class="close" onclick="closeModal('post-modal')">&times;</span>
        <h2>Opslag af ${post.author}</h2>
        <p>${post.text}</p>
        ${ post.image ? `<img src="${post.image}" style="max-width:100%; margin-top:1rem;">` : "" }
        ${ post.video ? `<video src="${post.video}" controls style="max-width:100%; margin-top:1rem;"></video>` : "" }
        <p><small>${new Date(post.timestamp).toLocaleString()}</small></p>
        <p>Likes: ${post.likes.length} 
          ${ currentUser ? `<button onclick="toggleLike(${post.id})">
            ${ post.likes.includes(currentUser.username) ? "Unlike" : "Like" }
          </button>` : "" }
        </p>
        <div id="comments-section">
          <h3>Kommentarer</h3>
          <div id="comments-list">
            ${ post.comments.length > 0 ? post.comments.map(c => `<p><strong>${c.author}</strong>: ${c.text} <small>${new Date(c.timestamp).toLocaleString()}</small></p>`).join("") : "<p>Ingen kommentarer endnu.</p>" }
          </div>
          ${ currentUser ? `
          <textarea id="new-comment-text" placeholder="Skriv en kommentar..."></textarea>
          <button onclick="addComment(${post.id})">Tilføj Kommentar</button>
          ` : "<p>Log ind for at kommentere.</p>" }
        </div>
        ${ (currentUser && currentUser.username === post.author) ? `<button onclick="editPost(${post.id})">Rediger Opslag</button>` : "" }
      `;
      document.getElementById("post-modal").style.display = "block";
    }
    
    function closeModal(modalId) {
      document.getElementById(modalId).style.display = "none";
    }
    
    function toggleLike(postId) {
      const post = posts.find(p => p.id === postId);
      if(!post || !currentUser) return;
      const index = post.likes.indexOf(currentUser.username);
      if(index === -1) {
        post.likes.push(currentUser.username);
      } else {
        post.likes.splice(index, 1);
      }
      savePosts();
      openPostModal(postId);
      renderPosts();
    }
    
    function addComment(postId) {
      const post = posts.find(p => p.id === postId);
      if(!post || !currentUser) return;
      const commentText = document.getElementById("new-comment-text").value;
      if(commentText.trim() === "") return alert("Skriv en kommentar!");
      const comment = {
        author: currentUser.username,
        text: commentText,
        timestamp: new Date().toISOString()
      };
      post.comments.push(comment);
      savePosts();
      openPostModal(postId);
    }
    
    // --- Søgning i opslag ---
    function searchPosts() {
      const query = (document.getElementById("search-input").value || document.getElementById("search-input-2").value).toLowerCase();
      const resultsContainer = document.getElementById("search-results");
      const filtered = posts.filter(post => post.text.toLowerCase().includes(query) || post.author.toLowerCase().includes(query));
      resultsContainer.innerHTML = "";
      if(query === "") {
        resultsContainer.innerHTML = "<p>Indtast et søgeord.</p>";
        return;
      }
      if(filtered.length === 0) {
        resultsContainer.innerHTML = "<p>Ingen resultater fundet.</p>";
        return;
      }
      filtered.forEach(post => {
        const div = document.createElement("div");
        div.className = "post";
        div.innerHTML = `<h2>${post.author} - ${new Date(post.timestamp).toLocaleString()}</h2><p>${post.text}</p>`;
        div.onclick = () => openPostModal(post.id);
        resultsContainer.appendChild(div);
      });
    }
    
    // --- Upload funktioner ---
    function handleUploads() {
      const filesInput = document.getElementById("upload-file");
      const previewContainer = document.getElementById("upload-preview");
      const files = filesInput.files;
      for (let i = 0; i < files.length; i++) {
        const file = files[i];
        const fileType = file.type;
        const reader = new FileReader();
        reader.onload = function(e) {
          const dataURL = e.target.result;
          if (fileType.startsWith("image/")) {
            const img = document.createElement("img");
            img.src = dataURL;
            previewContainer.appendChild(img);
            uploads.push({ id: Date.now(), type: "image", data: dataURL, fileName: file.name, timestamp: new Date().toISOString() });
          } else if (fileType.startsWith("video/")) {
            const video = document.createElement("video");
            video.src = dataURL;
            video.controls = true;
            previewContainer.appendChild(video);
            uploads.push({ id: Date.now(), type: "video", data: dataURL, fileName: file.name, timestamp: new Date().toISOString() });
          }
          saveUploads();
          renderCloudFiles();
        };
        reader.readAsDataURL(file);
      }
      filesInput.value = "";
    }
    
    function loadUploadsPreview() {
      const previewContainer = document.getElementById("upload-preview");
      previewContainer.innerHTML = "";
      uploads.forEach(upload => {
        if (upload.type === "image") {
          const img = document.createElement("img");
          img.src = upload.data;
          previewContainer.appendChild(img);
        } else if (upload.type === "video") {
          const video = document.createElement("video");
          video.src = upload.data;
          video.controls = true;
          previewContainer.appendChild(video);
        }
      });
    }
    
    // --- Cloud Files funktioner ---
    function renderCloudFiles() {
      const container = document.getElementById("cloud-files-list");
      container.innerHTML = "";
      const query = document.getElementById("cloud-files-search").value.toLowerCase();
      let filtered = uploads;
      if(query) {
        filtered = uploads.filter(file => file.fileName.toLowerCase().includes(query) || file.type.toLowerCase().includes(query));
      }
      if (filtered.length === 0) {
        container.innerHTML = "<p>Ingen filer fundet.</p>";
        return;
      }
      filtered.forEach(file => {
        const fileDiv = document.createElement("div");
        fileDiv.className = "file-item";
        fileDiv.onclick = () => showFileDetails(file);
        if(file.type === "image") {
          const img = document.createElement("img");
          img.src = file.data;
          fileDiv.appendChild(img);
        } else if(file.type === "video") {
          const video = document.createElement("video");
          video.src = file.data;
          video.controls = true;
          fileDiv.appendChild(video);
        }
        const delBtn = document.createElement("button");
        delBtn.innerText = "Slet";
        delBtn.onclick = (e) => {
          e.stopPropagation();
          deleteUpload(file.id);
        };
        fileDiv.appendChild(delBtn);
        const downloadBtn = document.createElement("button");
        downloadBtn.className = "download-btn";
        downloadBtn.innerText = "Download";
        downloadBtn.onclick = (e) => {
          e.stopPropagation();
          downloadFile(file);
        };
        fileDiv.appendChild(downloadBtn);
        container.appendChild(fileDiv);
      });
    }
    
    function searchCloudFiles() {
      renderCloudFiles();
    }
    
    function deleteUpload(fileId) {
      uploads = uploads.filter(file => file.id !== fileId);
      saveUploads();
      renderCloudFiles();
    }
    
    function showFileDetails(file) {
      const modalBody = document.getElementById("modal-body");
      modalBody.innerHTML = `
        <h3>${file.fileName}</h3>
        <p>Type: ${file.type}</p>
        <p>Uploadet: ${new Date(file.timestamp).toLocaleString()}</p>
      `;
      if(file.type === "image") {
        modalBody.innerHTML += `<img src="${file.data}" style="max-width:100%; margin-top:1rem;">`;
      } else if(file.type === "video") {
        modalBody.innerHTML += `<video src="${file.data}" controls style="max-width:100%; margin-top:1rem;"></video>`;
      }
      document.getElementById("file-modal").style.display = "block";
    }
    
    function downloadFile(file) {
      const a = document.createElement("a");
      a.href = file.data;
      a.download = file.fileName;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    }
    
    // --- Bøger funktioner (samme som før) ---
    function createBook() {
      const bookTitle = document.getElementById("book-title").value;
      if (bookTitle.trim() === "") {
        alert("Indtast en bogtitel!");
        return;
      }
      const newBook = { id: Date.now(), title: bookTitle, pages: [] };
      books.push(newBook);
      currentBook = newBook;
      saveBooks();
      renderBooks();
      document.getElementById("book-editor").style.display = "block";
      document.getElementById("current-book-title").innerText = "Rediger: " + currentBook.title;
      document.getElementById("book-form").reset();
    }
    
    function addPageToBook() {
      if (!currentBook) {
        alert("Vælg eller opret en bog først!");
        return;
      }
      const pageContent = document.getElementById("page-content").value;
      if (pageContent.trim() === "") {
        alert("Skriv noget indhold til siden!");
        return;
      }
      const bgColor = document.getElementById("page-bg").value;
      const textColor = document.getElementById("page-text-color").value;
      const page = { 
        id: Date.now(), 
        content: pageContent, 
        timestamp: new Date().toLocaleString(), 
        bg: bgColor, 
        textColor: textColor 
      };
      currentBook.pages.push(page);
      saveBooks();
      renderCurrentBookPages();
      document.getElementById("page-content").value = "";
    }
    
    function renderCurrentBookPages() {
      const container = document.getElementById("current-book-pages");
      container.innerHTML = "";
      currentBook.pages.forEach(page => {
        const pageElem = document.createElement("div");
        pageElem.className = "book-page";
        pageElem.style.backgroundColor = page.bg;
        pageElem.style.color = page.textColor;
        pageElem.innerHTML = `<strong>Side oprettet: ${page.timestamp}</strong><p>${page.content}</p>`;
        const editBtn = document.createElement("button");
        editBtn.innerText = "Rediger Side";
        editBtn.onclick = () => editPage(page.id);
        pageElem.appendChild(editBtn);
        container.appendChild(pageElem);
      });
    }
    
    function editPage(pageId) {
      let pageToEdit = currentBook.pages.find(p => p.id === pageId);
      if (!pageToEdit) return;
      currentEditingPageId = pageId;
      document.getElementById("edit-page-content").value = pageToEdit.content;
      document.getElementById("edit-page-bg").value = pageToEdit.bg;
      document.getElementById("edit-page-text").value = pageToEdit.textColor;
      document.getElementById("edit-page-section").style.display = "block";
    }
    
    function saveEditedPage() {
      let page = currentBook.pages.find(p => p.id === currentEditingPageId);
      if (!page) return;
      page.content = document.getElementById("edit-page-content").value;
      page.bg = document.getElementById("edit-page-bg").value;
      page.textColor = document.getElementById("edit-page-text").value;
      saveBooks();
      renderCurrentBookPages();
      cancelEditPage();
    }
    
    function cancelEditPage() {
      document.getElementById("edit-page-section").style.display = "none";
      currentEditingPageId = null;
    }
    
    function saveBookTitle() {
      let newTitle = document.getElementById("edit-book-title").value;
      if (newTitle.trim() === "") {
        alert("Indtast en gyldig titel!");
        return;
      }
      currentBook.title = newTitle;
      saveBooks();
      document.getElementById("current-book-title").innerText = "Rediger: " + currentBook.title;
      document.getElementById("edit-book-title").value = "";
      renderBooks();
    }
    
    function finishBook() {
      currentBook = null;
      document.getElementById("book-editor").style.display = "none";
      document.getElementById("current-book-pages").innerHTML = "";
      alert("Bogen er gemt!");
    }
    
    function renderBooks() {
      const container = document.getElementById("books-container");
      container.innerHTML = "";
      if (books.length === 0) {
        container.innerHTML = "<p>Ingen bøger endnu. Opret en ny bog for at komme i gang!</p>";
      }
      books.forEach(book => {
        const bookElem = document.createElement("div");
        bookElem.className = "book";
        let pagesHtml = "";
        book.pages.forEach(page => {
          pagesHtml += `<li>${page.content.substring(0, 30)}... (${page.timestamp})</li>`;
        });
        bookElem.innerHTML = `<h3>${book.title}</h3><p>${book.pages.length} side(r)</p><ul>${pagesHtml}</ul>`;
        const editBtn = document.createElement("button");
        editBtn.innerText = "Rediger Bog";
        editBtn.onclick = () => {
          currentBook = book;
          document.getElementById("current-book-title").innerText = "Rediger: " + book.title;
          document.getElementById("book-editor").style.display = "block";
          renderCurrentBookPages();
        };
        bookElem.appendChild(editBtn);
        container.appendChild(bookElem);
      });
    }
    
    // --- Auth funktioner ---
    function loginUser() {
      const username = document.getElementById("login-username").value.trim();
      const password = document.getElementById("login-password").value.trim();
      const msgElem = document.getElementById("auth-message");
      msgElem.innerText = "";
      if(username === "" || password === "") {
        msgElem.innerText = "Udfyld begge felter.";
        return;
      }
      const user = users.find(u => u.username === username && u.password === password);
      if(user) {
        currentUser = user;
        localStorage.setItem("currentUser", JSON.stringify(currentUser));
        msgElem.innerText = "Login succesfuldt!";
        updateAuthStatus();
        showSection("feed-section");
      } else {
        msgElem.innerText = "Forkert brugernavn eller adgangskode.";
      }
    }
    
    function registerUser() {
      const username = document.getElementById("register-username").value.trim();
      const password = document.getElementById("register-password").value.trim();
      const msgElem = document.getElementById("auth-message");
      msgElem.innerText = "";
      if(username === "" || password === "") {
        msgElem.innerText = "Udfyld begge felter.";
        return;
      }
      if(users.find(u => u.username === username)) {
        msgElem.innerText = "Brugernavnet er allerede optaget.";
        return;
      }
      const newUser = { username: username, password: password };
      users.push(newUser);
      saveUsers();
      msgElem.innerText = "Registrering succesfuld. Du kan nu logge ind.";
      document.getElementById("register-form").reset();
    }
    
    function logoutUser() {
      currentUser = null;
      localStorage.removeItem("currentUser");
      updateAuthStatus();
      showSection("feed-section");
    }
    
    function updateAuthStatus() {
      currentUser = JSON.parse(localStorage.getItem("currentUser"));
      const authBtnText = document.getElementById("auth-btn-text");
      if(currentUser) {
        authBtnText.innerText = "Logout (" + currentUser.username + ")";
      } else {
        authBtnText.innerText = "Login";
      }
    }
    
    function toggleAuth() {
      if(currentUser) {
        logoutUser();
      } else {
        showSection("login-section");
      }
    }
  </script>
</body>
</html>

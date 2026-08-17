# Import
from flask import Flask, render_template,request, redirect



app = Flask(__name__)

# İçerik sayfasını çalıştırma
@app.route('/')
def index():
    return render_template('index.html')


# Dinamik beceriler
@app.route('/', methods=['POST'])
def process_form():
    button_python = request.form.get('button_python')
    button_discord = request.form.get('button_discord')
    button_html = request.form.get('button_html')
    button_db = request.form.get('button_db')
    email = request.form.get('email')
    text = request.form.get('text')
    if email and text :
        with open("form.txt","a")as f:
            f.write(f"{email},{text}")
    return render_template('index.html', button_python=button_python,button_discord = button_discord,button_html = button_html,button_db = button_db)


if __name__ == "__main__":
    app.run(debug=True)

2. kod

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"
    />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <link rel="stylesheet" href="../static/css/style.css" />
    <title>Portföy</title>
  </head>
  <body>
    <header class="header">
      <nav class="header__nav main-nav">
        <ul class="main-nav__list main-list">
          <li class="main-list__item list-item">
            <a class="list-item__link" href="#home">HOME</a>
          </li>
          <li class="main-list__item list-item">
            <a class="list-item__link" href="#about">ABOUT</a>
          </li>
          <li class="main-list__item list-item">
            <a class="list-item__link" href="#skills">MY SKILLS</a>
          </li>
        </ul>
      </nav>
    </header>
    <main class="main">
      <!-- Önizleme bölümü -->
      <section class="main__home home" id="home">
        <h1 class="home__title">umut kaan sancaktar</h1>
        <p class="home__subtitle">WEB-DEVELOPER, PYTHON PROGRAMMER</p>
      </section>
      <!-- Hakkımda bölümü -->
      <section class="main__about about" id="about">
        <h2 class="about__title">ABOUT ME</h2>
        <div class="about__info info-block">
          <p class="info-block__text">
            python basic i bitirip orda projeler yaptım pyhton pro dada discord botu ve websiteleri yaptım 
          </p>
          <img
            class="info-block__img"
            src="../static/img/profile.png"
            alt="me"
            width="250"
            height="250"
          />
        </div>
      </section>
      <!-- Beceriler bölümü -->
      <section class="main__skills skills" id="skills">
        <h2 class="skills__title">MY SKILLS</h2>
        <form action="/" method="POST">
          <ul class="skills__list skills-list">
            <li class="skills-list__skill skill">
              <img
                class="skill__img"
                src="../static/img/python.png"
                alt="python"
                width="150"
                height="150"
              />
              <span class="skill__info">Skill info</span>
              <input class="skill__button" type="submit" name="button_python" value="SHOW PROJECT">
            </li>
            <li class="skills-list__skill skill">
              <img
                class="skill__img"
                src="../static/img/discord.png"
                alt="discord"
                width="150"
                height="150"
              />
              <span class="skill__info">Skill info</span>
              <input class="skill__button" type="submit" name="button_discord" value="SHOW PROJECT">
            </li>
            <li class="skills-list__skill skill">
              <img
                class="skill__img"
                src="../static/img/html.png"
                alt="html"
                width="150"
                height="150"
              />
              <span class="skill__info">Skill info</span>
              <input class="skill__button" type="submit" name="button_html" value="SHOW PROJECT">
            </li>
            <li class="skills-list__skill skill">
              <img
                class="skill__img"
                src="../static/img/db.webp"
                alt="SQL"
                width="150"
                height="150"
              />
              <span class="skill__info">Skill info</span>
              <input class="skill__button" type="submit" name="button_db" value="SHOW PROJECT">
            </li>
          </ul>
        </form>
        {% if button_python%}
          <div class="skills__project project" id="project">
              <img class="project__img" src="../static/img/python-project.png" alt="project" width="500">
              <a class="project__link" href="">GitHub'da aç</a>
          </div>
            {% elif button_discord%}
          <div class="skills__project project" id="project">
              <img class="project__img" src="../static/img/discord-project.png" alt="project" width="500">
              <a class="project__link" href="">GitHub'da aç</a>
          </div>
            {% elif button_html%}
          <div class="skills__project project" id="project">
              <img class="project__img" src="../static/img/html-project.png" alt="project" width="500">
              <a class="project__link" href="">GitHub'da aç</a>
          </div>
            {% elif button_db%}
          <div class="skills__project project" id="project">
              <img class="project__img" src="../static/img/db-project.png" alt="project" width="500">
              <a class="project__link" href="">GitHub'da aç</a>
          </div>
        {% endif %}
      </section>
      <!-- Geri bildirim formu -->
      <section class="main__feedback feedback" id="feedback">
        <h2 class="feedback__title">FEEDBACK</h2>
        <form action="" method="POST" class="feedback__form form">
          <label for="email">
            <input type="email" class="form__input" name="email" id="email" placeholder="enter E-mail" required>
          </label>
          <label for="text">
            <textarea name="text" class="form__input" id="text" cols="70" rows="10" required placeholder="Comment"></textarea>
          </label>
          <button class="form__button" type="submit">SEND</button>
        </form>
      </section>
    </main>
    <!-- Sosyal medya bağlantıları için bir alt bilgi -->
    <footer>

    </footer>
  </body>
</html>

3. Kod

@import url("https://fonts.googleapis.com/css2?family=Mulish:wght@400;700&display=swap");
body::-webkit-scrollbar {
  width: 0;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0 3%;
  font-family: "Mulish", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  letter-spacing: 0.2em;
  background: linear-gradient(180deg, #95e72b 0%, rgba(25, 82, 4, 0.8) 100%);
  color: #ffffff;
}

h1,
h2,
p {
  margin: 0;
}

h1,
h2 {
  font-weight: 700;
  font-size: 42px;
}

img {
  object-fit: contain;
}

a {
  text-decoration: none;
  color: inherit;
  transition: 0.2s;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.header {
  display: flex;
  justify-content: center;
  padding: 30px 0;
  width: 100%;
}

.main-list {
  display: flex;
  gap: 150px;
}

.list-item__link {
  position: relative;
  font-size: 26px;
  font-weight: 700;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.list-item__link::after {
  position: absolute;
  transition: 0.2s;
  content: "";
  border-radius: 10px;
  width: 55%;
  height: 3px;
  bottom: -12px;
  background: #e5e0e7;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.list-item__link:hover::after {
  width: 100%;
}

.home {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-image: url(../img/developer.png);
  background-size: cover;
  padding: 10vh 10vw 80vh 10vw;
  background-position: center bottom;
  gap: 20px;
}

.home__title {
  letter-spacing: 0.3em;
  font-size: 70px;
  text-align: center;
  color: #fdfdfd;
  line-height: 1;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.home__subtitle {
  font-weight: 700;
  font-size: 24px;
  text-align: center;
  line-height: 1;
}

.about {
  margin-bottom: 200px;
}

.about__title {
  font-size: 60px;
  position: relative;
  text-align: left;
  color: #eff1ef;
  line-height: 1;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  width: fit-content;
  margin-bottom: 60px;
}

.about__title::after {
  position: absolute;
  content: "";
  border-radius: 10px;
  width: 60%;
  height: 1px;
  bottom: -13px;
  background: #fff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.info-block {
  display: flex;
  justify-content: space-between;
}

.info-block__text {
  width: 40%;
}

.info-block__img {
  align-self: center;
}

.skills {
  margin-bottom: 200px;
  display: flex;
  flex-direction: column;
  gap: 80px;
}

.skills__title {
  font-size: 60px;
  position: relative;
  text-align: left;
  color: #d5cdda;
  line-height: 1;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  width: fit-content;
  margin-bottom: 20px;
}

.skills__title::after {
  position: absolute;
  content: "";
  border-radius: 10px;
  width: 60%;
  height: 1px;
  bottom: -13px;
  background: #fff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}


.skills-list {
  display: flex;
  justify-content: center;
  gap: 100px;
  flex-wrap: wrap;
}

.skill {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  text-align: center;
}

.skill__info {
  width: 150px;
}

.skill__button {
  font: inherit;
  font-weight: 700;
  color: #fff;
  background: none;
  border: none;
  cursor: pointer;
  transition: 0.2s;
}

.skill__button:hover {
  color: #f0eaf3;
}

.project {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 30px;
}

.project__img{
  border-radius: 30px;
}

.project__link {
  position: relative;
  font-size: 20px;
  font-weight: 700;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.project__link::after {
  position: absolute;
  transition: 0.2s;
  content: "";
  border-radius: 10px;
  width: 55%;
  height: 3px;
  bottom: -12px;
  background: #e7e2ea;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.project__link:hover::after {
  width: 100%;
}

.feedback {
  margin-bottom: 200px;
  display: flex;
  flex-direction: column;
  gap: 80px;
}

.feedback__title {
  font-size: 60px;
  position: relative;
  text-align: left;
  color: #d6d3d8;
  line-height: 1;
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  width: fit-content;
  margin-bottom: 20px;
}

.feedback__title::after {
  position: absolute;
  content: "";
  border-radius: 10px;
  width: 60%;
  height: 1px;
  bottom: -13px;
  background: #fff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.form {
  display: flex;
  flex-direction: column;
  align-self: center;
  align-items: center;
  gap: 20px;
}

.form label {
  width: 100%;
}

.form__input {
  width: 100%;
  font: inherit;
  background: #392657;
  border: 2px solid #a178b9;
  color: #fff;
  padding: 15px;
  border-radius: 10px;
  filter: drop-shadow(5px 5px 4px rgba(0, 0, 0, 0.25));
}

.form__input::placeholder {
  color: #fff;
}

.form__input:active,
.form__input:focus,
.form__input:focus-visible {
  border: none;
}


.form__button {
  font: inherit;
  font-weight: 800;
  color: #fff;
  background: linear-gradient(111.97deg, #CC8BF2 35.63%, rgba(204, 139, 242, 0) 150.16%);
  filter: drop-shadow(5px 5px 4px rgba(0, 0, 0, 0.25));
  padding: 15px 30px;
  border-radius: 20px;
  border: none;
  cursor: pointer;
}

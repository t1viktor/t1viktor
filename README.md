<h1 align="left">Olá, eu sou Victor Lima! 👋</h1>

###

<br clear="both">

<p align="left">Sobre mim<br>👨‍💻 Sou um entusiasta de tecnologia e estou dando meus primeiros passos como programador front-end. Estou animado para aprender e crescer na área de desenvolvimento web.</p>

###

<p align="left">🌱 Atualmente, estou buscando projetos emocionantes para contribuir e oportunidades como desenvolvedor front-end júnior.</p>

###

<h2 align="left">Habilidades</h2>

###

<p align="left">- 💻 Conhecimento em HTML, CSS e JavaScript.</p>

###

<h2 align="left">Projetos</h2>

###

<p align="left">Neste perfil, você encontrará meus projetos pessoais, desde pequenos exercícios até projetos mais elaborados. Estou aberto a colaborações e feedbacks!</p>

###

<h2 align="left">Contato</h2>

###

<p align="left">Gostaria de se conectar ou discutir oportunidades? Sinta-se à vontade para me contatar pelo [LinkedIn](https://www.linkedin.com/in/victor-lima-203250300/). Estou ansioso para conhecer novas pessoas e explorar novas oportunidades na área de desenvolvimento web.</p>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="40" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="40" alt="css3 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="40" alt="html5 logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" height="40" alt="figma logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" height="40" alt="linkedin logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" height="40" alt="nodejs logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="40" alt="react logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" height="40" alt="vscode logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sass/sass-original.svg" height="40" alt="sass logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/canva/canva-original.svg" height="40" alt="canva logo"  />
</div>

###

<div align="center">
  <img height="200" src="https://giffiles.alphacoders.com/171/171294.gif"  />
</div>

###

<img src="https://raw.githubusercontent.com/t1victor/t1victor/output/snake.svg" alt="Snake animation" />

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

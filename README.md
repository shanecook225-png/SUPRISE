<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Une Question Pour Toi ❤️</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&family=Pacifico&display=swap" rel="stylesheet">

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.3/dist/confetti.browser.min.js"></script>

<style>
/* =======================================
   DATE WITH ME ❤️
   STYLE.CSS
======================================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    font-family:'Poppins',sans-serif;
    overflow:hidden;
    background:linear-gradient(135deg,#ff4d8d,#b5179e,#7209b7,#3a0ca3);
    background-size:400% 400%;
    animation:bgAnimation 15s ease infinite;
    color:white;
    width:100vw;
    height:100vh;
}

@keyframes bgAnimation{
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

.screen{
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    opacity:0;
    visibility:hidden;
    transition:1s;
    padding:30px;
}

.screen.active{
    opacity:1;
    visibility:visible;
}

.content{
    width:100%;
    max-width:900px;
    text-align:center;
    padding:50px;
    border-radius:35px;
    background:rgba(255,255,255,.12);
    backdrop-filter:blur(20px);
    border:1px solid rgba(255,255,255,.25);
    box-shadow:0 20px 60px rgba(0,0,0,.35);
}

h1{
    font-size:3rem;
    font-weight:700;
    margin-bottom:20px;
    line-height:1.2;
}

h2{
    font-size:2rem;
    margin-bottom:20px;
}

h3{
    font-size:1.5rem;
    margin-bottom:15px;
    font-weight:400;
}

p{
    font-size:1.1rem;
    line-height:1.8;
    margin-top:20px;
    opacity:.95;
}

button{
    padding:18px 45px;
    margin-top:35px;
    border:none;
    outline:none;
    cursor:pointer;
    font-size:18px;
    font-weight:600;
    border-radius:60px;
    background:white;
    color:#ff2d75;
    transition:.35s;
    box-shadow:0 10px 30px rgba(0,0,0,.25);
}

button:hover{
    transform:translateY(-6px) scale(1.05);
    box-shadow:0 20px 40px rgba(0,0,0,.35);
}

.buttons{
    display:flex;
    justify-content:center;
    gap:40px;
    margin-top:50px;
    flex-wrap:wrap;
}

#yesBtn{
    background:#00d26a;
    color:white;
    font-size:22px;
    min-width:180px;
}

#yesBtn:hover{
    background:#00b85d;
}

#noBtn{
    background:#ff355e;
    color:white;
    font-size:22px;
    min-width:180px;
    position:relative;
}

.question{
    margin-top:40px;
    margin-bottom:20px;
}

#typingText{
    font-family:'Pacifico',cursive;
    font-size:2rem;
    color:#ffe082;
    min-height:80px;
}

.musicBtn{
    position:fixed;
    top:25px;
    right:25px;
    width:60px;
    height:60px;
    border-radius:50%;
    background:white;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:25px;
    cursor:pointer;
    color:#ff2d75;
    box-shadow:0 15px 30px rgba(0,0,0,.35);
    z-index:999;
    transition:.3s;
}

.musicBtn:hover{
    transform:scale(1.12);
}

.letter{
    max-width:900px;
    padding:60px;
    background:white;
    color:#444;
    border-radius:25px;
    box-shadow:0 25px 60px rgba(0,0,0,.35);
    line-height:2;
    text-align:center;
}

.letter h1{
    color:#ff2d75;
    font-family:'Pacifico',cursive;
    margin-bottom:35px;
}

.formCard{
    width:100%;
    max-width:700px;
    padding:45px;
    background:rgba(255,255,255,.15);
    backdrop-filter:blur(20px);
    border-radius:25px;
}

.inputBox{
    display:flex;
    flex-direction:column;
    margin-bottom:25px;
    text-align:left;
}

.inputBox label{
    margin-bottom:10px;
    font-weight:600;
}

input,
select{
    padding:15px;
    border:none;
    border-radius:15px;
    font-size:16px;
    outline:none;
}

.ticket{
    background:white;
    color:#333;
    padding:60px;
    border-radius:30px;
    max-width:750px;
    text-align:center;
    box-shadow:0 30px 70px rgba(0,0,0,.35);
}

.ticket h2{
    color:#ff2d75;
    margin-bottom:30px;
}

.resume{
    margin:30px 0;
}

.resume p{
    font-size:20px;
    margin:12px 0;
}

#funnyMessage{
    margin-top:30px;
    font-size:24px;
    font-weight:600;
    color:#ffe082;
    min-height:40px;
}

.hearts{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    overflow:hidden;
    pointer-events:none;
    z-index:-1;
}

@media(max-width:768px){
    .content{padding:30px;}
    h1{font-size:2rem;}
    h2{font-size:1.5rem;}
    p{font-size:1rem;}
    .buttons{flex-direction:column;gap:20px;}
    button{width:100%;}
    .letter{padding:30px;}
    .ticket{padding:35px;}
    .formCard{padding:30px;}
    .musicBtn{width:50px;height:50px;font-size:20px;}
}
</style>
</head>

<body>

<audio id="bgMusic" loop>
    <source src="assets/music/musique.mp3" type="audio/mpeg">
</audio>

<div class="musicBtn" id="musicBtn">🔊</div>

<div class="hearts"></div>

<!-- PAGE 1 -->
<section class="screen active" id="screen1">
<div class="content">
<h3>Salut 😊</h3>
<h1>J'ai quelque chose de très important à te demander...</h1>
<p>Mais avant... Promets-moi d'aller jusqu'au bout ❤️</p>
<button id="startBtn">Continuer</button>
</div>
</section>

<!-- PAGE 2 -->
<section class="screen" id="screen2">
<div class="content">
<h2 id="typingText"></h2>
<div class="question">
<h1>Ça te dirait un date avec moi ? 🥹❤️</h1>
</div>
<div class="buttons">
<button id="yesBtn">❤️ OUI</button>
<button id="noBtn">🙈 NON</button>
</div>
<div id="funnyMessage"></div>
</div>
</section>

<!-- PAGE 3 -->
<section class="screen" id="screen3">
<div class="content">
<div class="success">
<h1>🥹❤️</h1>
<h2>Tu viens de rendre ma journée incroyable.</h2>
<p>Merci d'avoir accepté. J'ai vraiment hâte de partager ce moment avec toi.</p>
</div>
<button id="openLetter">💌 Ouvrir une lettre</button>
</div>
</section>

<!-- PAGE 4 -->
<section class="screen" id="screen4">
<div class="letter">
<h1>Pour Toi ❤️</h1>
<p>
Je ne sais pas où cette aventure nous mènera.
Mais je sais une chose...
J'aimerais vraiment apprendre à mieux te connaître.
Sans pression.
Sans obligation.
Juste partager un beau moment avec toi.
Parce que je pense sincèrement que tu en vaux la peine.
Alors...
Est-ce qu'on se crée un joli souvenir ensemble ?
❤️
</p>
<button id="continueForm">Continuer</button>
</div>
</section>

<!-- PAGE 5 -->
<section class="screen" id="screen5">
<div class="formCard">
<h1>Notre Date ❤️</h1>

<div class="inputBox">
<label>📅 Choisis une date</label>
<input type="date" id="date">
</div>

<div class="inputBox">
<label>🕒 Choisis une heure</label>
<input type="time" id="heure">
</div>

<div class="inputBox">
<label>🍕 Que veux-tu faire ?</label>
<select id="activity">
<option>Pizza 🍕</option>
<option>Café ☕</option>
<option>Cinéma 🍿</option>
<option>Glace 🍨</option>
<option>Balade 🌅</option>
<option>Restaurant 🍽️</option>
<option>Bowling 🎳</option>
<option>Surprends-moi ❤️</option>
</select>
</div>

<div class="inputBox">
<label>📍 Où aimerais-tu aller ?</label>
<input type="text" placeholder="Exemple : Pizza Doudou" id="lieu">
</div>

<button id="finishBtn">Confirmer ❤️</button>
</div>
</section>

<!-- PAGE 6 -->
<section class="screen" id="screen6">
<div class="ticket">
<h1>🎉</h1>
<h2>Notre premier rendez-vous est confirmé ❤️</h2>
<div class="resume">
<p>📅 <span id="resumeDate"></span></p>
<p>🕒 <span id="resumeHeure"></span></p>
<p>🍕 <span id="resumeActivity"></span></p>
<p>📍 <span id="resumeLieu"></span></p>
</div>
<h3>J'ai vraiment hâte de te voir ❤️</h3>
<button onclick="location.reload()">Recommencer</button>
</div>
</section>

<script>
/*====================================
DATE WITH ME ❤️
====================================*/

const screens = document.querySelectorAll(".screen");

const startBtn = document.getElementById("startBtn");
const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");

const openLetter = document.getElementById("openLetter");
const continueForm = document.getElementById("continueForm");

const finishBtn = document.getElementById("finishBtn");

const music = document.getElementById("bgMusic");
const musicBtn = document.getElementById("musicBtn");

const funnyMessage = document.getElementById("funnyMessage");

const typingText = document.getElementById("typingText");

let musicPlaying = false;

/* WhatsApp : numéro qui recevra le message de confirmation */
const whatsappNumber = "2250100701007"; // +225 01 00 70 10 07

function envoyerWhatsApp(date, heure, activite, lieu){
    const message =
        "❤️ Nouveau rendez-vous confirmé !\n" +
        "📅 Date : " + date + "\n" +
        "🕒 Heure : " + heure + "\n" +
        "🍕 Activité : " + activite + "\n" +
        "📍 Lieu : " + lieu;

    const url = "https://wa.me/" + whatsappNumber + "?text=" + encodeURIComponent(message);

    window.open(url, "_blank");
}

function showScreen(id){
    screens.forEach(screen=>{
        screen.classList.remove("active");
    });
    document.getElementById(id).classList.add("active");
}

musicBtn.addEventListener("click",()=>{
    if(music.paused){
        music.play().catch(()=>{});
        musicBtn.innerHTML="🔊";
    }else{
        music.pause();
        musicBtn.innerHTML="🔇";
    }
});

startBtn.addEventListener("click",()=>{
    showScreen("screen2");
    if(!musicPlaying){
        music.play().catch(()=>{});
        musicPlaying=true;
    }
    typeWriter();
});

const text = "Avant de répondre... laisse-moi te dire quelque chose ❤️";
let index = 0;

function typeWriter(){
    typingText.innerHTML="";
    index=0;
    let timer = setInterval(()=>{
        typingText.innerHTML += text.charAt(index);
        index++;
        if(index>=text.length){
            clearInterval(timer);
        }
    },45);
}

/* COEURS FLOTTANTS */
const heartsContainer = document.querySelector(".hearts");

function createHeart(){
    const heart = document.createElement("span");
    heart.innerHTML="❤️";
    heart.style.position="absolute";
    heart.style.left=Math.random()*100+"vw";
    heart.style.bottom="-30px";
    heart.style.fontSize=(15+Math.random()*35)+"px";
    heart.style.opacity=Math.random();
    heart.style.animation="floatHeart "+(6+Math.random()*6)+"s linear forwards";
    heartsContainer.appendChild(heart);
    setTimeout(()=>{
        heart.remove();
    },12000);
}

setInterval(createHeart,350);

const style=document.createElement("style");
style.innerHTML=`
@keyframes floatHeart{
0%{transform:translateY(0) rotate(0deg); opacity:1;}
100%{transform:translateY(-120vh) rotate(360deg); opacity:0;}
}
`;
document.head.appendChild(style);

/* Messages du bouton NON */
const noMessages = [
"😅 Tu es vraiment sûre ?",
"🥺 Réfléchis encore...",
"👉 Promis, je suis sympa.",
"🍕 Et si je t'invitais à manger ?",
"😂 Tu n'abandonnes jamais hein ?",
"❤️ Donne-moi une chance.",
"😎 Je suis certain qu'on passerait un bon moment.",
"🙈 Bon... essaie encore.",
"🤣 Je vais continuer à m'enfuir !"
];

let noIndex = 0;

function moveNoButton(){
    const maxX = window.innerWidth - noBtn.offsetWidth - 40;
    const maxY = window.innerHeight - noBtn.offsetHeight - 40;

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    noBtn.style.position = "fixed";
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
    noBtn.style.transition = ".25s";

    funnyMessage.innerHTML = noMessages[noIndex % noMessages.length];
    noIndex++;

    const current = parseFloat(getComputedStyle(yesBtn).fontSize);
    yesBtn.style.fontSize = (current + 2) + "px";
    yesBtn.style.padding = (18 + noIndex * 1.5) + "px " + (45 + noIndex * 3) + "px";
}

noBtn.addEventListener("mouseenter", moveNoButton);
noBtn.addEventListener("click", moveNoButton);

window.addEventListener("resize",()=>{
    noBtn.style.left="";
    noBtn.style.top="";
    noBtn.style.position="relative";
});

yesBtn.addEventListener("click",()=>{
    try{
        if(typeof confetti === "function"){
            confetti({
                particleCount:250,
                spread:180,
                origin:{y:.6}
            });
        }
    }catch(e){
        console.warn("Confetti indisponible :", e);
    }

    setTimeout(()=>{
        showScreen("screen3");
    },900);
});

openLetter.addEventListener("click",()=>{
    showScreen("screen4");
});

continueForm.addEventListener("click",()=>{
    showScreen("screen5");
});

/* Petit effet d'apparition */
const observer = new MutationObserver(()=>{
    const active = document.querySelector(".screen.active");
    active.animate(
        [
            { opacity:0, transform:"scale(.95)" },
            { opacity:1, transform:"scale(1)" }
        ],
        { duration:500, easing:"ease" }
    );
});

observer.observe(document.body,{
    subtree:true,
    attributes:true,
    attributeFilter:["class"]
});

/* Validation du formulaire */
finishBtn.addEventListener("click",()=>{
    const date=document.getElementById("date").value;
    const heure=document.getElementById("heure").value;
    const activite=document.getElementById("activity").value;
    const lieu=document.getElementById("lieu").value;

    if(date==="" || heure==="" || lieu===""){
        alert("❤️ Remplis tous les champs avant de continuer.");
        return;
    }

    // Envoi automatique du message de confirmation sur WhatsApp
    envoyerWhatsApp(date, heure, activite, lieu);

    // Enregistrement optionnel dans Firebase, si configuré (voir note en bas de fichier)
    if(window.saveRendezVous){
        window.saveRendezVous({
            date, heure, activite, lieu, createdAt: new Date()
        });
    }

    document.getElementById("resumeDate").innerHTML=date;
    document.getElementById("resumeHeure").innerHTML=heure;
    document.getElementById("resumeActivity").innerHTML=activite;
    document.getElementById("resumeLieu").innerHTML=lieu;

    if(typeof confetti === "function"){
        for(let i=0;i<6;i++){
            setTimeout(()=>{
                try{
                    confetti({
                        particleCount:120,
                        spread:120,
                        startVelocity:60,
                        origin:{
                            x:Math.random(),
                            y:Math.random()*0.5
                        }
                    });
                }catch(e){
                    console.warn("Confetti indisponible :", e);
                }
            },i*350);
        }
    }

    let volume=music.volume;
    let fade=setInterval(()=>{
        if(volume>0.25){
            volume-=0.05;
            music.volume=volume;
        }else{
            clearInterval(fade);
        }
    },120);

    showScreen("screen6");
});

/* Animation du ticket */
const ticket=document.querySelector(".ticket");

const ticketObserver=new MutationObserver(()=>{
    if(document.getElementById("screen6").classList.contains("active")){
        ticket.animate(
        [
            { transform:"translateY(100px) scale(.8)", opacity:0 },
            { transform:"translateY(0) scale(1)", opacity:1 }
        ],
        { duration:900, easing:"ease-out" });
    }
});

ticketObserver.observe(document.body,{
    subtree:true,
    attributes:true,
    attributeFilter:["class"]
});

/* Boutons brillants */
setInterval(()=>{
    document.querySelectorAll("button").forEach(btn=>{
        btn.animate([
            { boxShadow:"0 0 0 rgba(255,255,255,0)" },
            { boxShadow:"0 0 35px rgba(255,255,255,.9)" },
            { boxShadow:"0 0 0 rgba(255,255,255,0)" }
        ],{ duration:1800 });
    });
},4000);

/* Pluie de coeurs finale */
function heartExplosion(){
    for(let i=0;i<40;i++){
        const heart=document.createElement("div");
        heart.innerHTML="❤️";
        heart.style.position="fixed";
        heart.style.left=Math.random()*100+"vw";
        heart.style.top="-50px";
        heart.style.fontSize=(20+Math.random()*25)+"px";
        heart.style.pointerEvents="none";
        heart.style.zIndex="99999";
        heart.style.transition="4s linear";

        document.body.appendChild(heart);

        setTimeout(()=>{
            heart.style.transform="translateY(120vh) rotate("+(Math.random()*720)+"deg)";
            heart.style.opacity="0";
        },50);

        setTimeout(()=>{
            heart.remove();
        },4200);
    }
}

const finalObserver=new MutationObserver(()=>{
    if(document.getElementById("screen6").classList.contains("active")){
        heartExplosion();
    }
});

finalObserver.observe(document.body,{
    subtree:true,
    attributes:true,
    attributeFilter:["class"]
});

console.log("❤️ Date With Me - Créé avec amour ❤️");
</script>

</body>
</html>

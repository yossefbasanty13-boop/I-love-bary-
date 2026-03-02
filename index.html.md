#   
<!doctype html>  
<html lang="en">  
<head>  
  <meta charset="utf-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1" />  
  <title>For You</title>  
  <style>  
    :root{  
      --bg:#0b0f1a;  
      --card:#111a2e;  
      --text:#f3f6ff;  
      --muted:#b9c3de;  
      --line:rgba(255,255,255,.12);  
      --accent:#ff5ca8;  
      --accent2:#6ae4ff;  
      --shadow: 0 18px 60px rgba(0,0,0,.45);  
      --radius:18px;  
    }  
    *{box-sizing:border-box}  
    body{  
      margin:0;  
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial;  
      color:var(--text);  
      background:  
        radial-gradient(900px 500px at 20% 0%, rgba(255,92,168,.22), transparent 55%),  
        radial-gradient(900px 500px at 80% 10%, rgba(106,228,255,.18), transparent 55%),  
        var(--bg);  
      min-height:100vh;  
      display:flex;  
      align-items:center;  
      justify-content:center;  
      padding:22px;  
    }  
    .wrap{width:min(1080px, 100%)}  
    .layout{  
      display:grid;  
      grid-template-columns: 1fr;  
      gap:16px;  
      align-items:start;  
    }  
    @media (min-width: 940px){  
      .layout{grid-template-columns: 1fr 320px;}  
    }  
  
    .topbar{  
      display:flex;  
      align-items:center;  
      justify-content:space-between;  
      gap:12px;  
      margin-bottom:14px;  
    }  
    .brand{font-weight:800; letter-spacing:.2px; opacity:.95;}  
    .pill{  
      border:1px solid var(--line);  
      background:rgba(255,255,255,.04);  
      padding:8px 12px;  
      border-radius:999px;  
      font-size:13px;  
      color:var(--muted);  
      display:flex;  
      gap:10px;  
      align-items:center;  
      backdrop-filter: blur(8px);  
    }  
    .dot{  
      width:10px;height:10px;border-radius:999px;  
      background:linear-gradient(90deg, var(--accent), var(--accent2));  
      box-shadow:0 0 18px rgba(255,92,168,.35);  
    }  
  
    .card{  
      background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.03));  
      border:1px solid var(--line);  
      border-radius:var(--radius);  
      box-shadow:var(--shadow);  
      overflow:hidden;  
    }  
    .header{padding:18px 18px 0 18px;}  
    .progress-wrap{  
      margin-top:10px;  
      border:1px solid var(--line);  
      background:rgba(0,0,0,.18);  
      border-radius:999px;  
      overflow:hidden;  
      height:12px;  
    }  
    .progress-bar{  
      height:100%;  
      width:0%;  
      background:linear-gradient(90deg, var(--accent), var(--accent2));  
      transition:width .35s ease;  
    }  
  
    .body{padding:18px; display:grid; gap:14px;}  
    .title{font-size:28px; line-height:1.12; margin:0;}  
    .apology{  
      color:var(--muted);  
      font-size:16px;  
      line-height:1.7;  
      margin:0;  
      white-space:pre-wrap;  
    }  
  
    .q{  
      padding:14px;  
      border:1px solid var(--line);  
      background:rgba(0,0,0,.14);  
      border-radius:16px;  
      display:grid;  
      gap:12px;  
    }  
    .q h2{margin:0; font-size:18px; letter-spacing:.1px;}  
    .btns{display:flex; flex-wrap:wrap; gap:10px;}  
  
    button{  
      border:1px solid var(--line);  
      background:rgba(255,255,255,.06);  
      color:var(--text);  
      padding:10px 14px;  
      border-radius:14px;  
      font-weight:650;  
      cursor:pointer;  
      transition: transform .05s ease, background .2s ease, border-color .2s ease;  
    }  
    button:hover{  
      background:rgba(255,255,255,.10);  
      border-color:rgba(255,255,255,.22);  
    }  
    button:active{transform: translateY(1px)}  
    .primary{  
      background:linear-gradient(90deg, rgba(255,92,168,.95), rgba(106,228,255,.80));  
      border-color:transparent;  
      color:#061018;  
    }  
    .danger{  
      background:rgba(255,107,107,.15);  
      border-color:rgba(255,107,107,.25);  
      color:var(--text);  
    }  
  
    .footer{  
      padding:0 18px 18px 18px;  
      color:var(--muted);  
      font-size:12px;  
      display:flex;  
      justify-content:space-between;  
      gap:12px;  
      flex-wrap:wrap;  
      opacity:.9;  
    }  
  
    /* Modal */  
    .overlay{  
      position:fixed;  
      inset:0;  
      background:rgba(0,0,0,.55);  
      display:none;  
      align-items:center;  
      justify-content:center;  
      padding:18px;  
      z-index:999;  
    }  
    .overlay.show{display:flex}  
    .modal{  
      width:min(560px, 100%);  
      background:linear-gradient(180deg, rgba(20,26,46,.98), rgba(12,15,26,.98));  
      border:1px solid var(--line);  
      border-radius:18px;  
      box-shadow:var(--shadow);  
      overflow:hidden;  
    }  
    .modal-head{  
      padding:14px 16px;  
      border-bottom:1px solid var(--line);  
      display:flex;  
      justify-content:space-between;  
      align-items:center;  
      gap:12px;  
    }  
    .modal-head strong{font-size:14px; letter-spacing:.2px}  
    .close-x{  
      background:transparent;  
      border:1px solid var(--line);  
      color:var(--muted);  
      padding:8px 10px;  
      border-radius:12px;  
      cursor:pointer;  
    }  
    .modal-body{padding:16px; display:grid; gap:12px}  
    .modal-body p{margin:0; color:var(--muted); line-height:1.6}  
  
    .toast{  
      position:fixed;  
      left:50%;  
      bottom:18px;  
      transform:translateX(-50%);  
      background:rgba(17,26,46,.95);  
      border:1px solid var(--line);  
      color:var(--text);  
      padding:10px 12px;  
      border-radius:14px;  
      box-shadow:var(--shadow);  
      display:none;  
      z-index:1000;  
      font-weight:650;  
    }  
    .toast.show{display:block}  
  
    /* Taylor Sidebar (Option A) */  
    .taylor{  
      position:sticky;  
      top:18px;  
      border:1px solid var(--line);  
      background:rgba(0,0,0,.14);  
      border-radius:18px;  
      padding:14px;  
      box-shadow: var(--shadow);  
    }  
    .taylor h3{  
      margin:0 0 10px 0;  
      font-size:14px;  
      letter-spacing:.2px;  
      color:var(--text);  
      display:flex;  
      align-items:center;  
      gap:10px;  
    }  
    .taylor h3 .spark{  
      width:10px;height:10px;border-radius:999px;  
      background:linear-gradient(90deg, var(--accent), var(--accent2));  
      box-shadow:0 0 18px rgba(106,228,255,.25);  
    }  
    .taylor .quote{  
      border:1px solid var(--line);  
      background:rgba(255,255,255,.05);  
      border-radius:14px;  
      padding:10px 12px;  
      color:var(--muted);  
      line-height:1.55;  
      margin:10px 0;  
    }  
    .taylor .tiny{  
      font-size:12px;  
      color:rgba(185,195,222,.9);  
      margin-top:10px;  
    }  
  </style>  
</head>  
  
<body>  
  <div class="wrap">  
    <div class="layout">  
  
      <!-- MAIN -->  
      <div>  
        <div class="topbar">  
          <div class="brand">For You</div>  
          <div class="pill"><span class="dot"></span><span id="stepLabel">Step 1 of 4</span></div>  
        </div>  
  
        <div class="card">  
          <div class="header">  
            <h1 class="title">Hey gorgeous.</h1>  
            <div class="progress-wrap" aria-label="Progress">  
              <div class="progress-bar" id="progressBar"></div>  
            </div>  
          </div>  
  
          <div class="body" id="mainArea">  
            <p class="apology" id="apologyText"></p>  
  
            <div class="q" id="step1">  
              <h2>did you love this website</h2>  
              <div class="btns">  
                <button class="primary" id="s1Yes">Yes</button>  
                <button class="danger" id="s1No">No</button>  
              </div>  
            </div>  
          </div>  
  
          <div class="footer">  
            <span id="statusText">Paste your endpoint URL to record responses.</span>  
            <span id="sessionText"></span>  
          </div>  
        </div>  
      </div>  
  
      <!-- TAYLOR SIDEBAR — Option A (Soft romantic / Lover-coded) -->  
      <aside class="taylor" aria-label="Taylor references">  
        <h3><span class="spark"></span>Taylor-coded notes</h3>  
  
        <!-- Short lyric snippets (kept very short) + paraphrases -->  
        <div class="quote">“Can I go where you go?”</div>  
        <div class="quote">“I’ve loved you three summers now…”</div>  
        <div class="quote">“You’re my… my… my…”</div>  
        <div class="quote">I want the kind of love that feels like home.</div>  
        <div class="quote">I’d choose you in every version of my life.</div>  
        <div class="quote">Let me prove it — not just say it.</div>  
  
        <div class="tiny">P.S. Consider this my Lover-era apology 🩷</div>  
      </aside>  
  
    </div>  
  </div>  
  
  <!-- Modal -->  
  <div class="overlay" id="overlay" role="dialog" aria-modal="true" aria-label="Question dialog">  
    <div class="modal">  
      <div class="modal-head">  
        <strong id="modalTitle">Question</strong>  
        <button class="close-x" id="closeModal" aria-label="Close">×</button>  
      </div>  
      <div class="modal-body">  
        <p id="modalQuestion"></p>  
        <div class="btns" id="modalButtons"></div>  
      </div>  
    </div>  
  </div>  
  
  <div class="toast" id="toast">wrong answer try again</div>  
  
  <script>  
    /***********************  
     * 1) SET YOUR ENDPOINT  
     * Paste your Google Apps Script Web App URL here to record responses to Google Sheets  
     ***********************/  
    const ENDPOINT_URL = ""; // <-- paste your endpoint URL here  
  
    /***********************  
     * Apology text (verbatim)  
     ***********************/  
    const APOLOGY_TEXT =  
`hey gorgeous I am I am sorry I’ve been upsetting you so much lately I hate that I have I will be making it upto you like I said before but the first thing you need to let me you know I love you more than anything and I am working so hard to make sure that you’re happy I have fell short in showing you how much I love you and how much you mean to me but it doesn’t mean that I stopped I love you and hope you can forgive me and I have dedicated this website to you`;  
  
    // Session id so you can track multiple runs  
    const sessionId = (crypto?.randomUUID?.() || ("sess_" + Math.random().toString(16).slice(2))) + "_" + Date.now();  
    document.getElementById("sessionText").textContent = "Session: " + sessionId.slice(0, 8);  
  
    // UI helpers  
    const overlay = document.getElementById("overlay");  
    const modalTitle = document.getElementById("modalTitle");  
    const modalQuestion = document.getElementById("modalQuestion");  
    const modalButtons = document.getElementById("modalButtons");  
    const closeModalBtn = document.getElementById("closeModal");  
    const toast = document.getElementById("toast");  
    const progressBar = document.getElementById("progressBar");  
    const stepLabel = document.getElementById("stepLabel");  
    const statusText = document.getElementById("statusText");  
  
    document.getElementById("apologyText").textContent = APOLOGY_TEXT;  
  
    const TOTAL_STEPS = 4; // 1=love website, 2=hate me, 3=date, 4=choose plan  
    let currentStep = 1;  
  
    function setProgress(step){  
      currentStep = step;  
      stepLabel.textContent = `Step ${step} of ${TOTAL_STEPS}`;  
      const pct = Math.round(((step-1) / (TOTAL_STEPS-1)) * 100); // 0, 33, 67, 100  
      progressBar.style.width = pct + "%";  
    }  
    setProgress(1);  
  
    function showToast(msg="wrong answer try again"){  
      toast.textContent = msg;  
      toast.classList.add("show");  
      setTimeout(() => toast.classList.remove("show"), 1800);  
    }  
  
    function openModal({title, question, buttons, allowClose=true}){  
      modalTitle.textContent = title;  
      modalQuestion.textContent = question;  
      modalButtons.innerHTML = "";  
  
      for (const b of buttons){  
        const btn = document.createElement("button");  
        btn.textContent = b.label;  
        btn.className = b.className || "";  
        btn.addEventListener("click", b.onClick);  
        modalButtons.appendChild(btn);  
      }  
  
      closeModalBtn.style.display = allowClose ? "inline-block" : "none";  
      overlay.classList.add("show");  
    }  
    function closeModal(){ overlay.classList.remove("show"); }  
    closeModalBtn.addEventListener("click", closeModal);  
    overlay.addEventListener("click", (e) => { if (e.target === overlay) closeModal(); });  
  
    /***********************  
     * Recording  
     ***********************/  
    const localLogKey = "apology_site_log_" + sessionId;  
    const log = [];  
  
    function addLog(eventName, value){  
      const entry = {  
        sessionId,  
        event: eventName,  
        value,  
        step: currentStep,  
        at: new Date().toISOString(),  
        userAgent: navigator.userAgent  
      };  
      log.push(entry);  
      try{ localStorage.setItem(localLogKey, JSON.stringify(log)); } catch {}  
  
      // Send to your endpoint  
      if (!ENDPOINT_URL){  
        statusText.textContent = "Paste your endpoint URL to record responses.";  
        return;  
      }  
  
      fetch(ENDPOINT_URL, {  
        method: "POST",  
        mode: "no-cors",  
        headers: {"Content-Type":"application/json"},  
        body: JSON.stringify(entry)  
      }).then(() => {  
        statusText.textContent = "Responses recorded ✔";  
      }).catch(() => {  
        statusText.textContent = "Couldn’t send (check endpoint). Saved locally as backup.";  
      });  
    }  
  
    /***********************  
     * Step logic  
     ***********************/  
    const s1Yes = document.getElementById("s1Yes");  
    const s1No  = document.getElementById("s1No");  
  
    s1No.addEventListener("click", () => {  
      addLog("q1_loveWebsite", "No");  
      showToast("wrong answer try again");  
    });  
  
    s1Yes.addEventListener("click", () => {  
      addLog("q1_loveWebsite", "Yes");  
      setProgress(2);  
  
      openModal({  
        title: "Question 2",  
        question: "so do you still hate me ?",  
        allowClose: false,  
        buttons: [  
          {  
            label: "Yes",  
            className: "primary",  
            onClick: () => {  
              addLog("q2_hateMe", "Yes");  
              closeModal();  
              setProgress(3);  
              step3();  
            }  
          },  
          {  
            label: "No",  
            className: "danger",  
            onClick: () => {  
              addLog("q2_hateMe", "No");  
              showToast("wrong answer try again");  
            }  
          }  
        ]  
      });  
    });  
  
    function step3(){  
      openModal({  
        title: "Question 3",  
        question: "will you go out with me on a date?",  
        allowClose: false,  
        buttons: [  
          {  
            label: "Yes",  
            className: "primary",  
            onClick: () => {  
              addLog("q3_date", "Yes");  
              closeModal();  
              setProgress(4);  
              step4();  
            }  
          },  
          {  
            label: "No",  
            className: "danger",  
            onClick: () => {  
              addLog("q3_date", "No");  
              showToast("wrong answer try again");  
            }  
          }  
        ]  
      });  
    }  
  
    function step4(){  
      openModal({  
        title: "Pick one",  
        question: "Choose the plan:",  
        allowClose: false,  
        buttons: [  
          {  
            label: "food and cuddle in the car",  
            className: "primary",  
            onClick: () => finish("food and cuddle in the car")  
          },  
          {  
            label: "movies and cuddle",  
            className: "primary",  
            onClick: () => finish("movies and cuddle")  
          }  
        ]  
      });  
    }  
  
    function finish(choice){  
      addLog("q4_choice", choice);  
      closeModal();  
  
      openModal({  
        title: "Thank you",  
        question: "thank you for your response and someone will reach out shortly based on these responses",  
        allowClose: true,  
        buttons: [  
          { label: "Close", onClick: () => closeModal() }  
        ]  
      });  
  
      addLog("completed", "Yes");  
    }  
  </script>  
</body>  
</html>  

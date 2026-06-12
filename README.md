[index.html](https://github.com/user-attachments/files/28903711/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GLOFER — Dashboard Financiero 2026</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.5.0/dist/chart.umd.js" integrity="sha384-iU8HYtnGQ8Cy4zl7gbNMOhsDTTKX02BTXptVP/vqAWIaTfM7isw76iyZCsjL2eVi" crossorigin="anonymous"></script>
<style>
:root{color-scheme:light;--navy:#1a3557;--blue:#2563a8;--blue-lt:#dbeafe;--green:#16a34a;--green-lt:#dcfce7;--red:#dc2626;--red-lt:#fee2e2;--amber:#d97706;--amber-lt:#fef3c7;--gray:#6b7280;--gray-lt:#f3f4f6;--border:#e5e7eb;--shadow:0 2px 8px rgba(0,0,0,.08)}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Segoe UI',Arial,sans-serif;background:#f0f4f8;color:#1f2937;font-size:13px}
.header{background:var(--navy);color:#fff;padding:16px 28px;display:flex;align-items:center;gap:16px}
.logo{width:52px;height:52px;background:#fff;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:900;color:var(--navy);font-size:22px;flex-shrink:0}
.header h1{font-size:18px;font-weight:700;line-height:1.3}
.header p{font-size:11px;opacity:.75;margin-top:2px}
.badge{background:rgba(255,255,255,.2);border-radius:20px;padding:3px 12px;font-size:11px;margin-top:5px;display:inline-block}
.wrap{max-width:1200px;margin:0 auto;padding:20px}
.tabs{display:flex;gap:4px;background:#fff;border-radius:10px;padding:6px;box-shadow:var(--shadow);margin-bottom:18px}
.tab{flex:1;text-align:center;padding:9px 6px;border-radius:7px;cursor:pointer;font-size:12px;font-weight:600;color:var(--gray);transition:all .2s;border:none;background:transparent}
.tab:hover{background:var(--blue-lt);color:var(--navy)}
.tab.active{background:var(--navy);color:#fff}
.kpi-grid{display:grid;grid-template-columns:repeat(5,1fr);gap:12px;margin-bottom:18px}
.kpi{background:#fff;border-radius:10px;padding:18px 14px;text-align:center;border:1px solid var(--border);box-shadow:var(--shadow)}
.kpi .kl{font-size:10px;color:var(--gray);font-weight:700;text-transform:uppercase;line-height:1.3;margin-bottom:6px}
.kpi .kv{font-size:22px;font-weight:900;margin:4px 0}
.kpi .ks{font-size:11px;color:var(--gray)}
.kpi.pos .kv{color:var(--green)} .kpi.neg .kv{color:var(--red)} .kpi.neu .kv{color:var(--blue)} .kpi.warn .kv{color:var(--amber)}
.card{background:#fff;border-radius:10px;box-shadow:var(--shadow);padding:20px;margin-bottom:18px}
.ct{font-size:13px;font-weight:700;color:var(--navy);border-bottom:2px solid var(--blue-lt);padding-bottom:8px;margin-bottom:14px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:18px}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin-bottom:18px}
.cw{position:relative;height:280px} .csm{position:relative;height:240px}
.rp{background:linear-gradient(135deg,#eff6ff,#f0fdf4);border:2px solid var(--blue-lt);border-radius:12px;padding:18px 22px;margin-bottom:18px}
.rp-t{font-size:13px;font-weight:700;color:var(--navy);margin-bottom:14px}
.rg{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:14px}
.ri label{display:block;font-size:11px;font-weight:700;color:var(--navy);text-transform:uppercase;margin-bottom:5px}
.ri input{width:100%;padding:10px 12px;border:2px solid var(--border);border-radius:8px;font-size:14px;font-weight:700;color:#1f2937;background:#fff;text-align:right;transition:border-color .2s}
.ri input:focus{outline:none;border-color:var(--blue);box-shadow:0 0 0 3px rgba(37,99,168,.1)}
.rc{font-size:11px;color:var(--green);margin-top:5px;font-weight:700}
.ra{display:flex;align-items:center;gap:12px;flex-wrap:wrap}
.bs{background:var(--green);color:#fff;border:none;border-radius:8px;padding:10px 22px;font-size:13px;font-weight:700;cursor:pointer;transition:all .2s}
.bs:hover{background:#15803d}
.bc{background:#fff;color:var(--gray);border:2px solid var(--border);border-radius:8px;padding:10px 18px;font-size:12px;font-weight:600;cursor:pointer}
.bc:hover{border-color:var(--red);color:var(--red)}
.sb{font-size:11px;font-weight:600;padding:6px 12px;border-radius:6px;background:var(--green-lt);color:#166534;display:none}
.rh{font-size:11px;color:var(--gray);background:rgba(255,255,255,.7);border-radius:6px;padding:7px 12px;margin-top:10px}
table.t{width:100%;border-collapse:collapse;font-size:11.5px}
table.t thead th{background:#1e3a5f;color:#fff;padding:7px 10px;text-align:right;font-weight:600;font-size:11px}
table.t thead th:first-child{text-align:left;width:35%}
table.t thead th.tm{font-size:10px;text-align:center;padding:5px 8px}
table.t thead th.act{background:#2563a8} table.t thead th.ant{background:#374151}
table.t td{padding:5px 10px;border-bottom:1px solid #f0f0f0;text-align:right}
table.t td:first-child{text-align:left}
table.t td.pc{font-size:10px;color:var(--gray)}
tr.sec td{background:#dbeafe;color:var(--navy);font-weight:700;font-size:11px;text-transform:uppercase;letter-spacing:.3px}
tr.sub td{background:#f0f7ff;font-weight:600;color:#1e40af;font-size:11px}
tr.tot td{background:var(--navy);color:#fff;font-weight:700;font-size:12px;padding:7px 10px}
tr.stot td{background:#e0f2fe;color:#0c4a6e;font-weight:700}
tr.util td{background:#166534;color:#fff;font-weight:700;font-size:13px;padding:8px 10px}
tr.perd td{background:var(--red);color:#fff;font-weight:700;font-size:13px;padding:8px 10px}
tr.ih td{background:#312e81;color:#fff;font-weight:700;padding:7px 10px;font-size:11px;text-transform:uppercase}
tr.ind td{background:#f5f3ff;padding:5px 10px}
tr.sp td{height:6px;background:#fff}
tr.in td:first-child{padding-left:22px}
.vp{color:var(--green);font-weight:600} .vn{color:var(--red);font-weight:600}
.msel{display:flex;gap:8px;flex-wrap:wrap;align-items:center}
.mb{padding:12px 22px;border-radius:10px;border:2px solid var(--border);cursor:pointer;font-size:13px;font-weight:700;background:#fff;color:var(--gray);transition:all .25s;box-shadow:0 2px 6px rgba(0,0,0,.06);letter-spacing:.3px}
.mb:hover{border-color:var(--blue);color:var(--blue);background:var(--blue-lt);transform:translateY(-2px);box-shadow:0 4px 12px rgba(37,99,168,.15)}
.mb.active{background:var(--navy);color:#fff;border-color:var(--navy);box-shadow:0 4px 14px rgba(26,53,87,.35);transform:translateY(-2px);font-size:14px}
.ytd{background:var(--navy);color:#fff;border-radius:10px;padding:18px 22px;display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:18px}
.yi .yl{font-size:10px;opacity:.75;font-weight:700;text-transform:uppercase;margin-bottom:5px;text-align:center}
.yi .yv{font-size:22px;font-weight:900;text-align:center} .yi .ys{font-size:11px;opacity:.7;margin-top:3px;text-align:center}
.ig{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-top:6px}
.ic{border-radius:12px;padding:18px 20px;display:flex;flex-direction:column;gap:8px;border-left:6px solid transparent;box-shadow:0 3px 12px rgba(0,0,0,.09);transition:transform .15s}
.ic:hover{transform:translateY(-2px)}
.ic.good{background:linear-gradient(135deg,#f0fdf4,#dcfce7);border-left-color:var(--green)}
.ic.bad{background:linear-gradient(135deg,#fff5f5,#fee2e2);border-left-color:var(--red)}
.ic.warn{background:linear-gradient(135deg,#fffbeb,#fef3c7);border-left-color:var(--amber)}
.ic.neu{background:linear-gradient(135deg,#eff6ff,#dbeafe);border-left-color:var(--blue)}
.ic .icl{font-size:12px;font-weight:700;color:#1f2937;line-height:1.3}
.ic .ics{font-size:10px;color:var(--gray);margin-top:2px}
.ic .icv{font-size:28px;font-weight:900;line-height:1}
.ic.good .icv{color:var(--green)} .ic.bad .icv{color:var(--red)} .ic.warn .icv{color:var(--amber)} .ic.neu .icv{color:var(--blue)}
.ic .icb{display:flex;align-items:center;justify-content:space-between;border-top:1px solid rgba(0,0,0,.07);padding-top:8px;margin-top:2px}
.ic .icvar{font-size:12px;font-weight:700} .ic .icbench{font-size:10px;color:var(--gray)}
.is{font-size:12px;font-weight:800;color:var(--navy);text-transform:uppercase;letter-spacing:.5px;margin:20px 0 10px;padding:6px 12px;background:var(--blue-lt);border-radius:6px}

.btn-send{background:linear-gradient(135deg,#16a34a,#15803d);color:#fff;border:none;border-radius:9px;padding:11px 20px;font-size:13px;font-weight:700;cursor:pointer;white-space:nowrap;flex-shrink:0;transition:all .2s}
.btn-send:hover{background:linear-gradient(135deg,#15803d,#166534);transform:translateY(-1px)}
.confirm-bar{background:#1e3a5f;color:#fff;padding:14px 28px;display:none;align-items:center;justify-content:space-between;gap:16px;flex-wrap:wrap}
.confirm-bar p{font-size:12px;line-height:1.5}
.confirm-bar p strong{font-size:13px;display:block;margin-bottom:3px}
.confirm-btns{display:flex;gap:10px;flex-shrink:0}
.btn-ok{background:#16a34a;color:#fff;border:none;border-radius:7px;padding:9px 20px;font-size:13px;font-weight:700;cursor:pointer}
.btn-ok:hover{background:#15803d}
.btn-cancel{background:transparent;color:#fff;border:2px solid rgba(255,255,255,.4);border-radius:7px;padding:9px 18px;font-size:12px;font-weight:600;cursor:pointer}
.btn-cancel:hover{background:rgba(255,255,255,.1)}
.send-msg{padding:10px 28px;font-size:12px;font-weight:600;display:none}
.send-msg.ok{background:#dcfce7;color:#166534}
.send-msg.err{background:#fee2e2;color:#dc2626}
</style>
</head>
<body>
<div class="header">
  <div class="logo">G</div>
  <div style="flex:1">
    <h1>GLOFER Distribuciones — Dashboard Financiero 2026</h1>
    <p>Andry Jiseth Puentes Meneses &nbsp;·&nbsp; NIT: 1.083.894.423-0</p>
    <span class="badge" id="badge"></span>
  </div>
  <button class="btn-send" onclick="showConfirm()">&#10003; Aprobar y Enviar Informe</button>
</div>

<div class="confirm-bar" id="confirm-bar">
  <p><strong>Confirmar envio &mdash; <span id="conf-mes"></span> 2026</strong>
  Para: anjiss_91@hotmail.com &middot; lincas444@gmail.com &nbsp;|&nbsp; CC: soportedeimpuestos@gmail.com</p>
  <div class="confirm-btns">
    <button class="btn-ok" onclick="doSend()">Confirmar y Enviar</button>
    <button class="btn-cancel" onclick="hideConfirm()">Cancelar</button>
  </div>
</div>
<div class="send-msg" id="send-msg"></div>

<div class="wrap">
<div class="rp">
  <div class="rp-t">💰 Ventas Remisiones / Otros Medios — Valor neto de IVA por mes</div>
  <div class="rg">
    <div class="ri"><label>Enero 2026</label><input type="text" id="rE" placeholder="0" oninput="fR(this,'ENERO')"><div class="rc" id="rcE"></div></div>
    <div class="ri"><label>Febrero 2026</label><input type="text" id="rF" placeholder="0" oninput="fR(this,'FEBRERO')"><div class="rc" id="rcF"></div></div>
    <div class="ri"><label>Marzo 2026</label><input type="text" id="rM" placeholder="0" oninput="fR(this,'MARZO')"><div class="rc" id="rcM"></div></div>
    <div class="ri"><label>Abril 2026</label><input type="text" id="rA" placeholder="0" oninput="fR(this,'ABRIL')"><div class="rc" id="rcA"></div></div>
  </div>
  <div class="ra">
    <button class="bs" onclick="saveR()">💾 Guardar Remisiones</button>
    <button class="bc" onclick="clearR()">🗑️ Limpiar</button>
    <button class="bs" style="background:#0891b2" onclick="exportarConDatos()">📤 Compartir con Datos</button>
    <span class="sb" id="sb">✅ Guardado</span>
  </div>
  <div class="rh">ℹ️ Costo ponderado <strong>81%</strong>. Guarde para que los valores persistan al reabrir.</div>
</div>
<div class="tabs">
  <button class="tab active" onclick="showTab('r')">📊 Resumen General</button>
  <button class="tab" onclick="showTab('m')">📋 Informe Comparativo</button>
  <button class="tab" onclick="showTab('g')">📈 Gráficos</button>
  <button class="tab" onclick="showTab('i')">📐 Indicadores</button>
</div>
<div id="tr">
  <div class="ytd" id="ytd"></div>
  <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;flex-wrap:wrap">
    <span style="font-size:12px;font-weight:700;color:var(--navy)">Detalle por mes:</span>
    <div class="msel" id="sr"></div>
  </div>
  <div class="kpi-grid" id="kg"></div>
  <div class="g2">
    <div class="card"><div class="ct">📈 Ventas · Costos · Gastos · Resultado</div><div class="cw"><canvas id="ce"></canvas></div></div>
    <div class="card"><div class="ct">🥧 Distribución del Ingreso — <span id="dm"></span></div><div class="cw"><canvas id="cd"></canvas></div></div>
  </div>
  <div class="g3">
    <div class="card"><div class="ct">📊 Margen Bruto %</div><div class="csm"><canvas id="cmb"></canvas></div></div>
    <div class="card"><div class="ct">📊 Margen Operacional %</div><div class="csm"><canvas id="cmo"></canvas></div></div>
    <div class="card"><div class="ct">📊 Gastos Operacionales</div><div class="csm"><canvas id="cg"></canvas></div></div>
  </div>
</div>
<div id="tm" style="display:none">
  <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;flex-wrap:wrap">
    <span style="font-size:12px;font-weight:700;color:var(--navy)">Mes actual:</span>
    <div class="msel" id="sm"></div>
  </div>
  <div style="background:#fff;border-radius:10px;overflow:hidden;box-shadow:var(--shadow)">
    <div style="background:var(--navy);color:#fff;padding:18px 24px;text-align:center">
      <div style="font-size:16px;font-weight:800;letter-spacing:.5px">GLOFER DISTRIBUCIONES GARZÓN</div>
      <div style="font-size:12px;opacity:.9;margin-top:3px">ANDRY JISETH PUENTES MENESES &nbsp;·&nbsp; NIT: 1.083.894.423-0</div>
      <div id="it" style="font-size:12px;font-weight:600;margin-top:7px;background:rgba(255,255,255,.15);display:inline-block;padding:3px 14px;border-radius:20px"></div>
    </div>
    <div style="overflow-x:auto"><table class="t" id="ti"></table></div>
  </div>
</div>
<div id="tg" style="display:none">
  <div class="g2">
    <div class="card"><div class="ct">📊 Comparativo Gastos Operacionales</div><div class="cw"><canvas id="cg2"></canvas></div></div>
    <div class="card"><div class="ct">📈 Evolución de Márgenes 2026</div><div class="cw"><canvas id="cmg"></canvas></div></div>
  </div>
  <div class="card"><div class="ct">📊 Estructura de Resultados por Mes</div><div style="position:relative;height:320px"><canvas id="cst"></canvas></div></div>
</div>
<div id="ti2" style="display:none">
  <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;flex-wrap:wrap">
    <span style="font-size:12px;font-weight:700;color:var(--navy)">Mes:</span>
    <div class="msel" id="si"></div>
  </div>
  <div class="card">
    <div class="ct">📐 Indicadores de Rentabilidad — <span id="iit"></span></div>
    <p style="font-size:11px;color:var(--gray);margin-bottom:4px">Valores en <strong>miles de pesos ($K)</strong>. Verde = favorable · Rojo = desfavorable.</p>
    <div class="is">📊 Márgenes de Rentabilidad</div><div class="ig" id="im"></div>
    <div class="is">💸 Estructura de Costos y Gastos</div><div class="ig" id="ico"></div>
    <div class="is">⚙️ Eficiencia Operacional</div><div class="ig" id="ie"></div>
    <div class="is">📉 Carga No Operacional</div><div class="ig" id="in"></div>
  </div>
  <div class="card"><div class="ct">📈 Evolución de Indicadores — 4 Meses 2026</div><div style="position:relative;height:320px"><canvas id="ci"></canvas></div></div>
  <div class="card"><div class="ct">📊 Estructura % sobre Ventas</div><div style="position:relative;height:320px"><canvas id="ces"></canvas></div></div>
</div>
</div>
<script>
const MS=['ENERO','FEBRERO','MARZO','ABRIL'],ML2=['Ene','Feb','Mar','Abr'];
const CPP=0.81,FX={GP:2000000,KI:4103641};
const RIDS={ENERO:'rE',FEBRERO:'rF',MARZO:'rM',ABRIL:'rA'};
const RCIDS={ENERO:'rcE',FEBRERO:'rcF',MARZO:'rcM',ABRIL:'rcA'};
const BASE={
  ENERO:  {vFE:129288242,desc:2618300, pila:413300, cont:910000,  ssgst:220000,sw:494918, pub:417478, leg:0,     mnt:0,     div:117647,suel:7820709, auxTr:1112623,ces:667407,ices:6675, prim:667407,vac:292142,auxi:415000,bonif:0,dot:0,arpV:41200, penV:939000, ccf:313300,med:400000,arrV:800000, trsp:12867300,gas:792531,iF:72, gF:1716,imp:79134},
  FEBRERO:{vFE:110051114,desc:1805211, pila:508300, cont:1300000, ssgst:230000,sw:527058, pub:250751, leg:0,     mnt:70000, div:0,      suel:8754525, auxTr:1245475,ces:833335,ices:8335, prim:833335,vac:364770,auxi:700000,bonif:0,dot:0,arpV:46000, penV:1051000,ccf:350500,med:0,     arrV:850000, trsp:12508000,gas:688483,iF:581,gF:0,   imp:79986},
  MARZO:  {vFE:132947081,desc:802290,  pila:526200, cont:1300000, ssgst:230000,sw:585114, pub:634480, leg:182100,mnt:394700,div:128992, suel:8754525, auxTr:1245475,ces:833335,ices:8335, prim:833335,vac:364770,auxi:0,     bonif:0,dot:0,arpV:46000, penV:1051000,ccf:350500,med:0,     arrV:850000, trsp:14852400,gas:801600,iF:360,gF:2926,imp:91812},
  ABRIL:  {vFE:202398862,desc:1274720, pila:508300, cont:1300000, ssgst:230000,sw:563876, pub:407203, leg:0,     mnt:0,     div:22857,  suel:8754525, auxTr:1245475,ces:833335,ices:8335, prim:833335,vac:364770,auxi:862077,bonif:0,dot:0,arpV:46000, penV:1051000,ccf:350500,med:0,     arrV:850000, trsp:15350600,gas:761000, iF:360,gF:652, imp:95893},
};
const RK='glofer_remi_2026';
function loadR(){try{const s=localStorage.getItem(RK);if(s)return JSON.parse(s);}catch(e){}return{ENERO:45781070,FEBRERO:52323344,MARZO:0,ABRIL:0};}
let REMI=loadR();
function saveR(){try{localStorage.setItem(RK,JSON.stringify(REMI));const b=document.getElementById('sb');b.style.display='inline-block';setTimeout(()=>b.style.display='none',3000);}catch(e){alert('Error: '+e);}}
function clearR(){if(!confirm('¿Limpiar remisiones?'))return;MS.forEach(m=>{REMI[m]=0;document.getElementById(RIDS[m]).value='0';document.getElementById(RCIDS[m]).textContent='';});localStorage.removeItem(RK);calc();ref();}
function initR(){MS.forEach(m=>{const v=REMI[m]||0;document.getElementById(RIDS[m]).value=v?v.toLocaleString('es-CO'):'0';if(v>0)document.getElementById(RCIDS[m]).textContent='→ Costo: $'+Math.round(v*CPP).toLocaleString('es-CO')+' (81%)';});}
function fR(inp,m){const n=parseInt(inp.value.replace(/[^0-9]/g,''))||0;inp.value=n?n.toLocaleString('es-CO'):'0';REMI[m]=n;document.getElementById(RCIDS[m]).textContent=n>0?'→ Costo: $'+Math.round(n*CPP).toLocaleString('es-CO')+' (81%)':'';calc();ref();}
function calcData(m){
  const b=BASE[m],r=REMI[m]||0,vTot=b.vFE+r,cFE=b.vFE*CPP-b.desc,cRemi=r*CPP,cTot=cFE+cRemi,UB=vTot-cTot;
  const icaB=Math.round(b.vFE*0.002/1000)*1000,icaD=Math.round(b.vFE*0.002*0.15/1000)*1000,ica=icaB-icaD;
  const tAdm=ica+b.pila+b.cont+b.ssgst+b.sw+b.pub+b.leg+b.mnt+b.div;
  const tPers=b.suel+b.auxTr+b.ces+b.ices+b.prim+b.vac+b.auxi+b.bonif+b.dot+b.arpV+b.penV+b.ccf+b.med;
  const tVta=tPers+b.arrV+b.trsp+b.gas,tGast=tAdm+tVta,UO=UB-tGast;
  const tNO=b.iF-b.gF-FX.GP-FX.KI-b.imp,UP=Math.round((UO+tNO)/100)*100;
  return{...b,ica,remi:r,vTot,cFE,cRemi,cTot,UB,tAdm,tPers,tVta,tGast,UO,gP:FX.GP,kI:FX.KI,tNO,UP,mgBruto:vTot?UB/vTot:0,mgOp:vTot?UO/vTot:0,mgNeto:vTot?UP/vTot:0};
}
let D={};function calc(){MS.forEach(m=>D[m]=calcData(m));}calc();
const K=n=>n===undefined?'—':Math.round(n/1000).toLocaleString('es-CO');
const FM=n=>{if(!n&&n!==0)return'—';const a=Math.abs(n);return(n<0?'-':'')+(a>=1e6?(a/1e6).toFixed(1)+'M':a>=1e3?Math.round(a/1000)+'K':a.toLocaleString('es-CO'));};
const FL=n=>{if(!n&&n!==0)return'$0';return(n<0?'($':'$')+Math.abs(Math.round(n)).toLocaleString('es-CO')+(n<0?')':'');};
const PCT=n=>(n*100).toFixed(1)+'%',P2=n=>(n*100).toFixed(2)+'%';
let cm='ABRIL',ct='r',iG2=false,iInd=false,CH={};
function dc(id){if(CH[id]){CH[id].destroy();delete CH[id];}}
function ref(){renderYTD();renderKPIs(cm);renderG(cm);renderT(cm);if(ct==='i'){renderInd(cm);renderChInd();}if(iG2)renderG2();}
function showTab(t){
  ct=t;
  ['r','m','g','i'].forEach((x,i)=>document.getElementById(['tr','tm','tg','ti2'][i]).style.display=x===t?'block':'none');
  document.querySelectorAll('.tab').forEach((el,i)=>el.classList.toggle('active',['r','m','g','i'][i]===t));
  if(t==='g'&&!iG2){renderG2();iG2=true;}
  if(t==='i'){renderInd(cm);if(!iInd){renderChInd();iInd=true;}}
}
document.getElementById('badge').textContent='📅 Datos al '+new Date().toLocaleDateString('es-CO',{day:'2-digit',month:'long',year:'numeric'});
function renderYTD(){
  const y={vTot:0,UB:0,tGast:0,UP:0};MS.forEach(m=>{y.vTot+=D[m].vTot;y.UB+=D[m].UB;y.tGast+=D[m].tGast;y.UP+=D[m].UP;});
  document.getElementById('ytd').innerHTML='<div class="yi"><div class="yl">📊 Ventas Acumuladas</div><div class="yv">$'+K(y.vTot)+'K</div><div class="ys">4 meses 2026</div></div>'+'<div class="yi"><div class="yl">💰 Util. Bruta Acum.</div><div class="yv">$'+K(y.UB)+'K</div><div class="ys">Margen: '+PCT(y.UB/y.vTot)+'</div></div>'+'<div class="yi"><div class="yl">💸 Gastos Acum.</div><div class="yv">$'+K(y.tGast)+'K</div><div class="ys">Ene–Abr</div></div>'+'<div class="yi"><div class="yl">'+(y.UP>=0?'✅':'⚠️')+' Resultado Acum.</div><div class="yv" style="color:'+(y.UP>=0?'#86efac':'#fca5a5')+'">$'+K(y.UP)+'K</div><div class="ys">Período</div></div>';
}
function buildSel(id,cb){
  const c=document.getElementById(id);c.querySelectorAll('.mb').forEach(b=>b.remove());
  MS.forEach(m=>{const b=document.createElement('button');b.className='mb'+(m===cm?' active':'');b.textContent=m;b.dataset.m=m;b.onclick=()=>{cm=m;document.querySelectorAll('.mb').forEach(x=>x.classList.toggle('active',x.dataset.m===m));cb(m);};c.appendChild(b);});
}
function renderKPIs(m){
  const d=D[m],mc=d.mgOp>0.05?'pos':d.mgOp>0?'warn':'neg';
  document.getElementById('kg').innerHTML='<div class="kpi neu"><div class="kl">Ventas Totales</div><div class="kv">$'+K(d.vTot)+'K</div><div class="ks">FE: $'+K(d.vFE)+'K · Remi: $'+K(d.remi)+'K</div></div><div class="kpi pos"><div class="kl">Utilidad Bruta</div><div class="kv">$'+K(d.UB)+'K</div><div class="ks">Margen: '+PCT(d.mgBruto)+'</div></div><div class="kpi '+mc+'"><div class="kl">Util. Operacional</div><div class="kv">$'+K(d.UO)+'K</div><div class="ks">Margen Op: '+PCT(d.mgOp)+'</div></div><div class="kpi '+(d.UP>=0?'pos':'neg')+'"><div class="kl">Resultado del Período</div><div class="kv">$'+K(d.UP)+'K</div><div class="ks">Mg Neto: '+PCT(d.mgNeto)+'</div></div><div class="kpi warn"><div class="kl">Gastos Operac.</div><div class="kv">$'+K(d.tGast)+'K</div><div class="ks">Adm: $'+K(d.tAdm)+'K · Vtas: $'+K(d.tVta)+'K</div></div>';
}
function renderT(m){
  const idx=MS.indexOf(m),mA=idx>0?MS[idx-1]:null,d=D[m],dA=mA?D[mA]:null;
  document.getElementById('it').textContent='INFORME DE RESULTADOS — '+m+(mA?' vs '+mA:'')+' 2026';
  const pc=(v,t)=>t?'('+(Math.abs(v)/t*100).toFixed(1)+'%)':'';
  const vr=(a,b)=>{if(!dA||b===undefined)return'';const v=a-b;return'<span class="'+(v>=0?'vp':'vn')+'">'+(v>=0?'+':'')+FL(v)+'</span>';};
  const vp=(a,b)=>{if(!dA||b===undefined||b===0)return'';const p=(a-b)/Math.abs(b)*100;return'<span class="'+(p>=0?'vp':'vn')+'">'+(p>=0?'+':'')+p.toFixed(1)+'%</span>';};
  const C=dA?7:3,sp='<tr class="sp"><td colspan="'+C+'"></td></tr>',sec=l=>'<tr class="sec"><td colspan="'+C+'">'+l+'</td></tr>';
  const row=(cls,lbl,va,vb,ind)=>{
    if(va===undefined||va===null||va==='')return'<tr class="'+cls+'"><td'+(ind?' class="in"':'')+'>'+lbl+'</td><td colspan="'+(C-1)+'"></td></tr>';
    return'<tr class="'+cls+'"><td'+(ind?' class="in"':'')+'>'+lbl+'</td><td>'+FL(va)+'</td><td class="pc">'+pc(va,d.vTot)+'</td>'+(dA?'<td>'+(vb!==undefined?FL(vb):'—')+'</td><td class="pc">'+(vb!==undefined?pc(vb,dA.vTot):'')+'</td><td>'+vr(va,vb)+'</td><td class="pc">'+vp(va,vb)+'</td>':'')+'</tr>';
  };
  let h='<thead><tr><th rowspan="2" style="text-align:left">Concepto</th><th colspan="2" class="tm act">'+m+'</th>'+(dA?'<th colspan="2" class="tm ant">'+mA+'</th><th colspan="2" class="tm">Variación</th>':'')+'</tr><tr><th>Valor</th><th>% Vtas</th>'+(dA?'<th>Valor</th><th>% Vtas</th><th>$ Var</th><th>% Var</th>':'')+'</tr></thead><tbody>';
  h+=sec('INGRESOS OPERACIONALES');
  h+=row('in','Ventas Factura Electrónica (Neto)',d.vFE,dA?.vFE,true);
  if(d.remi>0||(dA&&dA.remi>0))h+=row('in','Ventas Remisiones / Otros Medios',d.remi,dA?.remi,true);
  h+=row('tot','TOTAL INGRESOS',d.vTot,dA?.vTot);h+=sp;
  h+=sec('COSTO DE VENTAS');
  h+=row('in','Costo Ventas FE (81%)',d.cFE,dA?.cFE,true);
  if(d.remi>0||(dA&&dA.remi>0))h+=row('in','Costo Ventas Remisiones (81%)',d.cRemi,dA?.cRemi,true);
  h+=row('in','(-) Desc. Pronto Pago Cta. 143507',-d.desc,dA?-dA.desc:undefined,true);
  h+=row('tot','TOTAL COSTO DE VENTAS',d.cTot,dA?.cTot);h+=row('stot','UTILIDAD BRUTA',d.UB,dA?.UB);h+=sp;
  h+=sec('GASTOS OPERACIONALES DE ADMINISTRACIÓN');
  h+=row('in','ICA (2‰ FE, desc. 15%)',d.ica,dA?.ica,true);
  if(d.pila>0||(dA&&dA.pila>0))h+=row('in','Aportes Seg. Social Admón. (510568-570)',d.pila,dA?.pila,true);
  h+=row('in','Honorarios — Asesoría Financiera (511030)',d.cont,dA?.cont,true);
  if(d.ssgst>0||(dA&&dA.ssgst>0))h+=row('in','Diseño e Impl. SSGST (51103501)',d.ssgst,dA?.ssgst,true);
  if(d.sw>0||(dA&&dA.sw>0))h+=row('in','Software / Procesamiento (513520)',d.sw,dA?.sw,true);
  h+=row('in','Servicios Públicos (513525-595)',d.pub,dA?.pub,true);
  if(d.leg>0||(dA&&dA.leg>0))h+=row('in','Gastos Legales (514010)',d.leg,dA?.leg,true);
  if(d.mnt>0||(dA&&dA.mnt>0))h+=row('in','Mantenimiento (514520-525)',d.mnt,dA?.mnt,true);
  if(d.div>0||(dA&&dA.div>0))h+=row('in','Gastos Diversos (519530-595)',d.div,dA?.div,true);
  h+=row('tot','TOTAL GASTOS ADMÓN.',d.tAdm,dA?.tAdm);h+=sp;
  h+=sec('GASTOS OPERACIONALES DE VENTAS');
  h+=row('sub','PERSONAL DE VENTAS',d.tPers,dA?.tPers);
  h+=row('in','Sueldos y Salarios (520506)',d.suel,dA?.suel,true);
  if(d.auxTr>0||(dA&&dA.auxTr>0))h+=row('in','Auxilio de Transporte (520527)',d.auxTr,dA?.auxTr,true);
  if(d.ces>0||(dA&&dA.ces>0))h+=row('in','Cesantías (520530)',d.ces,dA?.ces,true);
  if(d.ices>0||(dA&&dA.ices>0))h+=row('in','Intereses Cesantías (520533)',d.ices,dA?.ices,true);
  if(d.prim>0||(dA&&dA.prim>0))h+=row('in','Prima de Servicios (520536)',d.prim,dA?.prim,true);
  if(d.vac>0||(dA&&dA.vac>0))h+=row('in','Vacaciones (520539)',d.vac,dA?.vac,true);
  if(d.auxi>0||(dA&&dA.auxi>0))h+=row('in','Auxilio / Subsidio (520545)',d.auxi,dA?.auxi,true);
  if(d.penV>0||(dA&&dA.penV>0))h+=row('in','Pensión Voluntaria (520570)',d.penV,dA?.penV,true);
  if(d.ccf>0||(dA&&dA.ccf>0))h+=row('in','Caja Compensación (520572)',d.ccf,dA?.ccf,true);
  if(d.med>0||(dA&&dA.med>0))h+=row('in','Medicina Prepagada (520584)',d.med,dA?.med,true);
  if(d.arpV>0||(dA&&dA.arpV>0))h+=row('in','ARP Ventas (520568)',d.arpV,dA?.arpV,true);
  h+=row('in','Arrendamiento Local (522010)',d.arrV,dA?.arrV,true);
  h+=row('in','Transporte y Flete (523550)',d.trsp,dA?.trsp,true);
  if(d.gas>0||(dA&&dA.gas>0))h+=row('in','Gasolina (525515)',d.gas,dA?.gas,true);
  h+=row('tot','TOTAL GASTOS VENTAS',d.tVta,dA?.tVta);
  h+=row('tot','TOTAL GASTOS OPERACIONALES',d.tGast,dA?.tGast);
  h+=row(d.UO>=0?'stot':'perd','UTILIDAD OPERACIONAL',d.UO,dA?.UO);h+=sp;
  h+='<tr class="ih"><td colspan="'+C+'">INGRESOS / GASTOS NO OPERACIONALES</td></tr>';
  if(d.iF>0||(dA&&dA.iF>0))h+=row('ind','Ingresos Financieros (421005-020)',d.iF,dA?.iF);
  h+=row('ind','(-) Gastos Financieros (530515-550)',-d.gF,dA?-dA.gF:undefined);
  h+=row('ind','(-) Gastos Personales',-d.gP,dA?-dA.gP:undefined);
  h+=row('ind','(-) Cuotas Préstamos (K+I)',-d.kI,dA?-dA.kI:undefined);
  if(d.imp>0||(dA&&dA.imp>0))h+=row('ind','(-) Impuestos asumidos (531520)',-d.imp,dA?-dA.imp:undefined);
  h+=row(d.tNO>=0?'stot':'ind','RESULTADO NO OPERACIONAL',d.tNO,dA?.tNO);h+=sp;
  h+=row(d.UP>=0?'util':'perd','RESULTADO DEL PERÍODO',d.UP,dA?.UP);
  const I=ci(m),IA=mA?ci(mA):null;
  const ir=(lbl,v,va,gh)=>{const dt=va!==undefined?v-va:null;const ds=dt!==null?'<span class="'+(gh?dt>=0?'vp':'vn':dt<=0?'vp':'vn')+'">'+(dt>=0?'+':'')+P2(Math.abs(dt))+'</span>':'—';return'<tr class="ind"><td>'+lbl+'</td><td>'+P2(v)+'</td><td></td>'+(dA?'<td>'+(va!==undefined?P2(va):'—')+'</td><td></td><td>'+ds+'</td><td></td>':'')+'</tr>';};
  h+=sp+'<tr class="ih"><td colspan="'+C+'">INDICADORES DE RENTABILIDAD</td></tr>';
  h+=ir('Margen Bruto',I.mgBruto,IA?.mgBruto,true)+ir('Margen Operacional',I.mgOp,IA?.mgOp,true)+ir('Margen Neto del Período',I.mgNeto,IA?.mgNeto,true);
  h+=ir('% Costo de Ventas / Ventas',I.pctCosto,IA?.pctCosto,false)+ir('% Gastos Admón. / Ventas',I.pctAdm,IA?.pctAdm,false)+ir('% Personal / Ventas',I.pctPers,IA?.pctPers,false);
  h+=ir('% Transporte / Ventas',I.pctTrsp,IA?.pctTrsp,false)+ir('% Gastos Ventas / Ventas',I.pctVtas,IA?.pctVtas,false)+ir('Carga No Operacional / Ventas',I.pesoCargaNO,IA?.pesoCargaNO,false);
  h+='</tbody>';document.getElementById('ti').innerHTML=h;
}
function ci(m){const d=D[m],v=d.vTot;return{mgBruto:d.UB/v,mgOp:d.UO/v,mgNeto:d.UP/v,mgEBITDA:(d.UO+d.gF)/v,relGastUB:d.tGast/d.UB,pctGastTotal:d.tGast/v,pctCosto:d.cTot/v,pctAdm:d.tAdm/v,pctVtas:d.tVta/v,pctPers:d.tPers/v,pctTrsp:d.trsp/v,pctArr:d.arrV/v,pctICA:d.ica/v,pctHon:(d.cont+d.ssgst)/v,pctPub:d.pub/v,pctGF:d.gF/v,pctGP:d.gP/v,pctKI:d.kI/v,pesoCargaNO:(d.gF+d.gP+d.kI+d.imp)/v,UBK:Math.round(d.UB/1000),UOK:Math.round(d.UO/1000),UPK:Math.round(d.UP/1000),tGastK:Math.round(d.tGast/1000)};}
function iCard(lbl,sub,val,valA,gh,extra){
  const dt=valA!==undefined?val-valA:null;
  const cls=gh?(val>0.10?'good':val>0.05?'warn':'bad'):(val<0.05?'good':val<0.15?'warn':'bad');
  const cv=dt!==null?(gh?dt>=0?'vp':'vn':dt<=0?'vp':'vn'):'';
  const vs=dt!==null?'<span class="icvar '+cv+'">'+(dt>=0?'▲':'▼')+' '+P2(Math.abs(dt))+' vs ant.</span>':'<span class="icvar" style="color:#9ca3af">Sin comparativo</span>';
  const ex=extra!==undefined?'<span class="icbench">$'+Math.abs(extra).toLocaleString('es-CO')+'K</span>':'';
  return'<div class="ic '+cls+'"><div><div class="icl">'+lbl+'</div><div class="ics">'+sub+'</div></div><div class="icv">'+P2(val)+'</div><div class="icb">'+vs+ex+'</div></div>';
}
function renderInd(m){
  const idx=MS.indexOf(m),mA=idx>0?MS[idx-1]:null,I=ci(m),IA=mA?ci(mA):null;
  document.getElementById('iit').textContent=m+(mA?' vs '+mA:'')+' 2026';
  document.getElementById('im').innerHTML=iCard('Margen Bruto','Util. Bruta / Ventas',I.mgBruto,IA?.mgBruto,true,I.UBK)+iCard('Margen Operacional','Util. Op. / Ventas',I.mgOp,IA?.mgOp,true,I.UOK)+iCard('Margen Neto','Resultado / Ventas',I.mgNeto,IA?.mgNeto,true,I.UPK)+iCard('Margen EBITDA aprox.','(UO+GF) / Ventas',I.mgEBITDA,IA?.mgEBITDA,true)+iCard('Cobertura de Gastos','Gastos / Util. Bruta',I.relGastUB,IA?.relGastUB,false)+iCard('Carga Total Gastos','Total Gastos / Ventas',I.pctGastTotal,IA?.pctGastTotal,false,I.tGastK);
  document.getElementById('ico').innerHTML=iCard('% Costo de Ventas','Costo Total / Ventas',I.pctCosto,IA?.pctCosto,false)+iCard('% Gastos Admón.','Gs. Admón. / Ventas',I.pctAdm,IA?.pctAdm,false)+iCard('% Gastos Ventas','Gs. Ventas / Ventas',I.pctVtas,IA?.pctVtas,false)+iCard('% Personal','Gs. Personal / Ventas',I.pctPers,IA?.pctPers,false)+iCard('% Transporte','Flete y Transp. / Ventas',I.pctTrsp,IA?.pctTrsp,false)+iCard('% Arrendamiento','Arrend. / Ventas',I.pctArr,IA?.pctArr,false);
  document.getElementById('ie').innerHTML=iCard('% ICA','Ind. y Comercio / Ventas',I.pctICA,IA?.pctICA,false)+iCard('% Honorarios','Cont.+SSGST / Ventas',I.pctHon,IA?.pctHon,false)+iCard('% Serv. Públicos','Agua, Energía, Tel. / Ventas',I.pctPub,IA?.pctPub,false);
  document.getElementById('in').innerHTML=iCard('% Gastos Financieros','GF / Ventas',I.pctGF,IA?.pctGF,false)+iCard('% Gastos Personales','GP / Ventas',I.pctGP,IA?.pctGP,false)+iCard('% Cuotas Préstamos','K+I / Ventas',I.pctKI,IA?.pctKI,false)+iCard('Carga No Operacional','(GF+GP+KI+Imp) / Ventas',I.pesoCargaNO,IA?.pesoCargaNO,false);
}
function renderChInd(){
  const Is=MS.map(m=>ci(m));
  dc('ci');CH['ci']=new Chart(document.getElementById('ci'),{type:'line',data:{labels:ML2,datasets:[{label:'Margen Bruto %',data:Is.map(i=>+(i.mgBruto*100).toFixed(2)),borderColor:'#22c55e',backgroundColor:'rgba(34,197,94,.1)',fill:true,tension:.4,pointRadius:5},{label:'Margen Op. %',data:Is.map(i=>+(i.mgOp*100).toFixed(2)),borderColor:'#3b82f6',backgroundColor:'rgba(59,130,246,.1)',fill:true,tension:.4,pointRadius:5},{label:'Margen Neto %',data:Is.map(i=>+(i.mgNeto*100).toFixed(2)),borderColor:'#f59e0b',backgroundColor:'rgba(245,158,11,.1)',fill:true,tension:.4,pointRadius:5},{label:'Carga Gastos %',data:Is.map(i=>+(i.pctGastTotal*100).toFixed(2)),borderColor:'#ef4444',fill:false,tension:.4,pointRadius:5,borderDash:[5,3]}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:11}}},tooltip:{callbacks:{label:ctx=>' '+ctx.dataset.label+': '+ctx.parsed.y.toFixed(2)+'%'}}},scales:{y:{ticks:{callback:v=>v+'%',font:{size:10}}}}}});
  dc('ces');CH['ces']=new Chart(document.getElementById('ces'),{type:'bar',data:{labels:ML2,datasets:[{label:'% Costo',data:Is.map(i=>+(i.pctCosto*100).toFixed(1)),backgroundColor:'rgba(239,68,68,.7)'},{label:'% Gs.Admón.',data:Is.map(i=>+(i.pctAdm*100).toFixed(1)),backgroundColor:'rgba(245,158,11,.7)'},{label:'% Personal',data:Is.map(i=>+(i.pctPers*100).toFixed(1)),backgroundColor:'rgba(59,130,246,.7)'},{label:'% Transporte',data:Is.map(i=>+(i.pctTrsp*100).toFixed(1)),backgroundColor:'rgba(14,165,233,.6)'},{label:'% Carga NO',data:Is.map(i=>+(i.pesoCargaNO*100).toFixed(1)),backgroundColor:'rgba(156,163,175,.6)'}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:10}}},tooltip:{callbacks:{label:ctx=>' '+ctx.dataset.label+': '+ctx.parsed.y.toFixed(1)+'%'}}},scales:{x:{stacked:true},y:{stacked:true,ticks:{callback:v=>v+'%',font:{size:10}},max:120}}}});
}
function renderG(m){
  document.getElementById('dm').textContent=m;const d=D[m];
  dc('ce');CH['ce']=new Chart(document.getElementById('ce'),{type:'bar',data:{labels:ML2,datasets:[{label:'Ventas',data:MS.map(x=>D[x].vTot),backgroundColor:'rgba(37,99,168,.7)',order:2},{label:'Costo',data:MS.map(x=>D[x].cTot),backgroundColor:'rgba(220,38,38,.5)',order:2},{label:'Gastos',data:MS.map(x=>D[x].tGast),backgroundColor:'rgba(217,119,6,.5)',order:2},{label:'Resultado',data:MS.map(x=>D[x].UP),type:'line',borderColor:'#16a34a',backgroundColor:'rgba(22,163,74,.15)',pointRadius:5,fill:true,order:1,tension:.4}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:11}}},tooltip:{callbacks:{label:ctx=>{const v=ctx.parsed.y,tot=D[MS[ctx.dataIndex]].vTot;return' '+ctx.dataset.label+': $'+Math.abs(Math.round(v/1000)).toLocaleString('es-CO')+'K'+(tot?' ('+( Math.abs(v)/tot*100).toFixed(1)+'%)':'');}}}},scales:{y:{ticks:{callback:v=>FM(v),font:{size:10}}}}}});
  const dd=[d.cTot,d.tAdm,d.tVta,Math.max(0,d.UO)],dT=dd.reduce((a,b)=>a+b,0);
  dc('cd');CH['cd']=new Chart(document.getElementById('cd'),{type:'doughnut',data:{labels:['Costo Ventas','Gastos Admón.','Gastos Ventas','Util. Operacional'],datasets:[{data:dd,backgroundColor:['#ef4444','#f59e0b','#3b82f6','#22c55e'],borderWidth:2}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{position:'bottom',labels:{font:{size:10}}},tooltip:{callbacks:{label:ctx=>' '+ctx.label+': $'+Math.round(ctx.parsed/1000).toLocaleString('es-CO')+'K ('+( ctx.parsed/dT*100).toFixed(1)+'%)'}}}}}); 
  dc('cmb');CH['cmb']=new Chart(document.getElementById('cmb'),{type:'bar',data:{labels:ML2,datasets:[{label:'Mg Bruto %',data:MS.map(x=>+(D[x].mgBruto*100).toFixed(2)),backgroundColor:MS.map(x=>D[x].mgBruto>0.15?'rgba(22,163,74,.7)':D[x].mgBruto>0.08?'rgba(217,119,6,.7)':'rgba(220,38,38,.7)')}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:ctx=>' Mg Bruto: '+ctx.parsed.y.toFixed(2)+'%'}}},scales:{y:{ticks:{callback:v=>v+'%',font:{size:10}},suggestedMin:0,suggestedMax:25}}}});
  dc('cmo');CH['cmo']=new Chart(document.getElementById('cmo'),{type:'bar',data:{labels:ML2,datasets:[{label:'Mg Op %',data:MS.map(x=>+(D[x].mgOp*100).toFixed(2)),backgroundColor:MS.map(x=>D[x].mgOp>0.05?'rgba(22,163,74,.7)':D[x].mgOp>0?'rgba(217,119,6,.7)':'rgba(220,38,38,.7)')}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:{callbacks:{label:ctx=>' Mg Op: '+ctx.parsed.y.toFixed(2)+'%'}}},scales:{y:{ticks:{callback:v=>v+'%',font:{size:10}}}}}});
  dc('cg');CH['cg']=new Chart(document.getElementById('cg'),{type:'bar',data:{labels:ML2,datasets:[{label:'Gastos Admón.',data:MS.map(x=>D[x].tAdm),backgroundColor:'rgba(99,102,241,.7)'},{label:'Personal Ventas',data:MS.map(x=>D[x].tPers),backgroundColor:'rgba(59,130,246,.6)'},{label:'Otros Ventas',data:MS.map(x=>D[x].tVta-D[x].tPers),backgroundColor:'rgba(147,197,253,.7)'}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:10}}},tooltip:{callbacks:{label:ctx=>{const v=ctx.parsed.y,tot=D[MS[ctx.dataIndex]].vTot;return' '+ctx.dataset.label+': $'+Math.round(v/1000).toLocaleString('es-CO')+'K ('+( v/tot*100).toFixed(1)+'% ventas)';}}}},scales:{x:{stacked:true},y:{stacked:true,ticks:{callback:v=>FM(v),font:{size:10}}}}}});
}
function renderG2(){
  dc('cg2');CH['cg2']=new Chart(document.getElementById('cg2'),{type:'bar',data:{labels:ML2,datasets:[{label:'ICA',data:MS.map(x=>D[x].ica),backgroundColor:'rgba(109,40,217,.6)'},{label:'Honorarios',data:MS.map(x=>D[x].cont+D[x].ssgst),backgroundColor:'rgba(79,70,229,.6)'},{label:'Serv. Públicos',data:MS.map(x=>D[x].pub),backgroundColor:'rgba(99,102,241,.6)'},{label:'Personal',data:MS.map(x=>D[x].tPers),backgroundColor:'rgba(59,130,246,.6)'},{label:'Transporte',data:MS.map(x=>D[x].trsp),backgroundColor:'rgba(14,165,233,.6)'},{label:'Arrend.',data:MS.map(x=>D[x].arrV),backgroundColor:'rgba(6,182,212,.6)'},{label:'Otros',data:MS.map(x=>D[x].div+D[x].mnt+D[x].leg+D[x].sw),backgroundColor:'rgba(20,184,166,.6)'}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:10}}},tooltip:{callbacks:{label:ctx=>{const v=ctx.parsed.y,tot=D[MS[ctx.dataIndex]].vTot;return' '+ctx.dataset.label+': $'+Math.round(v/1000).toLocaleString('es-CO')+'K ('+( v/tot*100).toFixed(1)+'% ventas)';}}}},scales:{x:{stacked:true},y:{stacked:true,ticks:{callback:v=>FM(v),font:{size:10}}}}}});
  dc('cmg');CH['cmg']=new Chart(document.getElementById('cmg'),{type:'line',data:{labels:ML2,datasets:[{label:'Mg Bruto %',data:MS.map(x=>+(D[x].mgBruto*100).toFixed(2)),borderColor:'#22c55e',backgroundColor:'rgba(34,197,94,.1)',fill:true,tension:.4,pointRadius:5},{label:'Mg Op. %',data:MS.map(x=>+(D[x].mgOp*100).toFixed(2)),borderColor:'#3b82f6',backgroundColor:'rgba(59,130,246,.1)',fill:true,tension:.4,pointRadius:5},{label:'Mg Neto %',data:MS.map(x=>+(D[x].mgNeto*100).toFixed(2)),borderColor:'#f59e0b',backgroundColor:'rgba(245,158,11,.1)',fill:true,tension:.4,pointRadius:5}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:11}}},tooltip:{callbacks:{label:ctx=>' '+ctx.dataset.label+': '+ctx.parsed.y.toFixed(2)+'%'}}},scales:{y:{ticks:{callback:v=>v+'%',font:{size:10}}}}}});
  dc('cst');CH['cst']=new Chart(document.getElementById('cst'),{type:'bar',data:{labels:ML2,datasets:[{label:'Util. Bruta',data:MS.map(x=>D[x].UB),backgroundColor:'rgba(22,163,74,.7)'},{label:'(-) Gs. Admón.',data:MS.map(x=>-D[x].tAdm),backgroundColor:'rgba(220,38,38,.6)'},{label:'(-) Gs. Ventas',data:MS.map(x=>-D[x].tVta),backgroundColor:'rgba(239,68,68,.4)'},{label:'Resultado Op.',data:MS.map(x=>D[x].UO),type:'line',borderColor:'#1d4ed8',pointRadius:6,pointBackgroundColor:'#1d4ed8',tension:.3,fill:false}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{labels:{font:{size:11}}},tooltip:{callbacks:{label:ctx=>{const v=ctx.parsed.y,tot=D[MS[ctx.dataIndex]].vTot;return' '+ctx.dataset.label+': $'+Math.abs(Math.round(v/1000)).toLocaleString('es-CO')+'K ('+( Math.abs(v)/tot*100).toFixed(1)+'% ventas)';}}}},scales:{y:{ticks:{callback:v=>FM(v),font:{size:10}}}}}});
}

const EMAILS_TO=['anjiss_91@hotmail.com','lincas444@gmail.com'];
const EMAIL_CC='soportedeimpuestos@gmail.com';

function showConfirm(){
  document.getElementById('conf-mes').textContent=cm;
  const bar=document.getElementById('confirm-bar');
  bar.style.display='flex';
  document.getElementById('send-msg').style.display='none';
}
function hideConfirm(){
  document.getElementById('confirm-bar').style.display='none';
}

function doSend(){
  const d=D[cm];
  const msg=document.getElementById('send-msg');
  document.getElementById('confirm-bar').style.display='none';

  const pct=n=>(n*100).toFixed(1)+'%';
  const p2=n=>(n*100).toFixed(2)+'%';
  const fmt=n=>n.toLocaleString('es-CO');
  const L=s=>s+'\r\n';

  const asunto=encodeURIComponent('Informe de Resultados GLOFER — '+cm+' 2026');
  let b='';
  b+=L('GLOFER DISTRIBUCIONES GARZON');
  b+=L('Andry Jiseth Puentes Meneses | NIT: 1.083.894.423-0');
  b+=L('INFORME DE RESULTADOS — '+cm+' 2026');
  b+=L('');
  b+=L('INGRESOS');
  b+=L('  Ventas FE:              $'+fmt(d.vFE)+' ('+pct(d.vFE/d.vTot)+')');
  if(d.remi>0) b+=L('  Ventas Remisiones:      $'+fmt(d.remi)+' ('+pct(d.remi/d.vTot)+')');
  b+=L('  TOTAL VENTAS:           $'+fmt(d.vTot));
  b+=L('');
  b+=L('RESULTADOS');
  b+=L('  Utilidad Bruta:         $'+fmt(d.UB)+'  '+pct(d.mgBruto));
  b+=L('  Total Gastos Operac.:   $'+fmt(d.tGast)+'  '+pct(d.tGast/d.vTot));
  b+=L('  Utilidad Operacional:   $'+fmt(d.UO)+'  '+pct(d.mgOp));
  b+=L('  RESULTADO DEL PERIODO:  $'+fmt(d.UP)+'  '+pct(d.mgNeto));
  b+=L('');
  b+=L('INDICADORES DE RENTABILIDAD');
  b+=L('  Margen Bruto:           '+p2(d.UB/d.vTot));
  b+=L('  Margen Operacional:     '+p2(d.UO/d.vTot));
  b+=L('  Margen Neto:            '+p2(d.UP/d.vTot));
  b+=L('  % Costo / Ventas:       '+p2(d.cTot/d.vTot));
  b+=L('  % Gastos Admón:         '+p2(d.tAdm/d.vTot));
  b+=L('  % Personal / Ventas:    '+p2(d.tPers/d.vTot));
  b+=L('  % Transporte / Ventas:  '+p2(d.trsp/d.vTot));
  b+=L('');
  b+=L('Generado: '+new Date().toLocaleDateString('es-CO',{day:'2-digit',month:'long',year:'numeric'}));

  const mailto='mailto:anjiss_91@hotmail.com,lincas444@gmail.com'
    +'?cc=soportedeimpuestos@gmail.com'
    +'&subject='+asunto
    +'&body='+encodeURIComponent(b);

  window.location.href=mailto;

  msg.className='send-msg ok';
  msg.style.display='block';
  msg.textContent='Abriendo correo con informe de '+cm+' 2026 prellenado. Revise y haga clic en Enviar desde su cliente de correo.';
}

function exportarConDatos(){
  const datos=JSON.stringify(REMI);
  const meses=Object.entries(REMI).filter(([,v])=>v>0).map(([m,v])=>m+': $'+Math.round(v).toLocaleString('es-CO')).join('\n');
  if(!meses){alert('No hay remisiones ingresadas. Ingrese los valores primero.');return;}
  if(!confirm('Se generará una copia del Dashboard con las remisiones:\n\n'+meses+'\n\nLa persona que reciba el archivo verá estos valores al abrirlo.\n\n¿Continuar?'))return;
  let html='<!DOCTYPE html>\n'+document.documentElement.outerHTML;
  const marker='const RK=\'glofer_remi_2026\';';
  const inyeccion='// ── DATOS PRE-CARGADOS AL COMPARTIR ──\n(function(){try{localStorage.setItem(\'glofer_remi_2026\',\''+datos.replace(/'/g,"\\'")+'\')}catch(e){}})();\n// ── FIN ──\n';
  if(html.includes(marker)){
    html=html.replace(marker,inyeccion+marker);
  } else {alert('Error interno al generar el archivo.');return;}
  const fecha=new Date().toLocaleDateString('es-CO').replace(/\//g,'-');
  const a=document.createElement('a');
  a.href=URL.createObjectURL(new Blob([html],{type:'text/html;charset=utf-8'}));
  a.download='Dashboard_GLOFER_'+fecha+'.html';
  a.click();
}

initR();calc();renderYTD();
buildSel('sr',m=>{renderKPIs(m);renderG(m);});
buildSel('sm',m=>renderT(m));
buildSel('si',m=>renderInd(m));
renderKPIs(cm);renderG(cm);renderT(cm);
</script>
</body>
</html>

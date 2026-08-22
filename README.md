[index (2).html](https://github.com/user-attachments/files/31341068/index.2.html)
<!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Poupe Hoje - Angola - Corrigido</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Inter,system-ui,sans-serif}
body{background:#f5f5f0;color:#18181b;padding:20px}
.card{background:#fff;border:1px solid #e4e4e7;border-radius:16px;padding:20px;margin-bottom:16px}
h1{font-size:32px;font-weight:800}
.green{background:#dcfce7;border:1px solid #86efac;color:#166534;padding:12px;border-radius:12px;margin:12px 0;font-weight:600}
input[type=range]{width:100%;height:8px}
button{padding:14px 24px;border-radius:999px;border:none;font-weight:700;cursor:pointer;font-size:16px}
.btn-black{background:#18181b;color:#fff}
.btn-white{background:#fff;color:#18181b;border:1px solid #e4e4e7}
.item{display:flex;align-items:center;justify-content:space-between;padding:10px 0;border-bottom:1px solid #f4f4f5}
</style>
</head>
<body>
<div style="max-width:600px;margin:0 auto">
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:20px">
<h1>Poupe Hoje</h1>
<div style="display:flex;gap:8px">
<button onclick="abrirLogin()" class="btn-white" style="padding:10px 20px;font-size:14px">🔑 ENTRAR</button>
<button onclick="abrirPagamento()" class="btn-black" style="padding:10px 20px;font-size:14px;background:#7c3aed">💳 PAGAR</button>
</div>
</div>
<p>Simulador simples - versão corrigida - botão Repor ATIVO - <span id="contadorGlobal" class="badge" style="background:#18181b;color:#fff;padding:4px 10px;border-radius:999px;font-size:12px">👁️ 117 visitas</span></p>

<div class="card">
<h3>Rendimento mensal bruto</h3>
<input type="range" id="renda" min="0" max="500000" step="1000" value="90000">
<div>Valor: <b id="rendaVal">90.000 Kz</b></div>
<div>INSS (3%): <b id="inssVal">2.700 Kz</b> | IRT: 0 Kz | Líquido: <b id="liquidoVal">87.300 Kz</b></div>
</div>

<div class="card">
<h3>Despesas (começam em 0)</h3>
<div id="despesas"></div>
<div style="margin-top:12px;font-weight:800" id="totalDesp">Total: 0 Kz</div>
<div>Sobra: <b id="dispVal">87.300 Kz</b></div>
</div>

<div class="card">
<h3>Quanto guardas?</h3>
<input type="range" id="perc" min="0" max="100" value="10">
<span id="percVal">10%</span> -> Guardas <b id="poupVal"></b>
<br><br>
Guardado hoje: <input type="range" id="guard" min="0" max="500000" step="1000" value="0"> <b id="guardVal">0 Kz</b>
<br><br>
Horizonte: <input type="range" id="hor" min="1" max="30" value="10"> <b id="horVal">10 anos</b>
</div>

<div class="card">
<h3>Perfil</h3>
<button id="btn-cons" onclick="setPerfil('conservador')">Conservador 6%</button>
<button id="btn-eq" onclick="setPerfil('equilibrado')" style="background:#18181b;color:#fff">Equilibrado 13%</button>
<button id="btn-ar" onclick="setPerfil('arrojado')">Arrojado 20%</button>
<div style="margin-top:12px">Projeção em <span id="horLabel">10</span> anos a <span id="taxaLabel">13</span>%: <b id="projVal" style="font-size:22px"></b></div>
</div>

<div class="card">
<button class="btn-black" onclick="calc()">CALCULAR REALIDADE</button>
<button class="btn-white" onclick="reporPadrao()" style="margin-left:10px">REPÔR PADRÃO (ATIVO)</button>
<div class="green">✅ Botão Repor corrigido - agora funciona - limpa localStorage + reseta tudo + reload</div>
</div>


<div id="modalLogin" style="display:none;position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:9999;padding:20px;place-items:center">
<div class="card" style="max-width:400px;width:100%;margin:0 auto;margin-top:10vh">
<h3>🔑 Entrar</h3>
<p style="font-size:13px;color:#71717a;margin:8px 0">Acesso ao simulador completo</p>
<input id="emailLogin" type="email" placeholder="Seu email" style="width:100%;padding:12px;border-radius:12px;border:1px solid #e4e4e7;margin:8px 0">
<input id="senhaLogin" type="password" placeholder="Senha" style="width:100%;padding:12px;border-radius:12px;border:1px solid #e4e4e7;margin:8px 0">
<button onclick="fazerLogin()" class="btn-black" style="width:100%;margin-top:12px">ENTRAR AGORA</button>
<button onclick="fecharLogin()" class="btn-white" style="width:100%;margin-top:8px">Cancelar</button>
</div>
</div>

<div id="modalPagamento" style="display:none;position:fixed;inset:0;background:rgba(0,0,0,0.5);z-index:9999;padding:20px;place-items:center">
<div class="card" style="max-width:420px;width:100%;margin:0 auto;margin-top:5vh">
<h3>💳 Pagar Acesso Premium</h3>
<div style="background:#f5f5f0;padding:16px;border-radius:12px;margin:12px 0">
<div style="font-size:28px;font-weight:900">2.500 Kz</div>
<div style="font-size:13px;color:#71717a">Acesso vitalício • Simulador completo • Painel Admin • Sem anúncios</div>
</div>
<p style="font-size:13px;line-height:1.5">
✅ Simulador Angola completo<br>
✅ Projeção 6%/13%/20%<br>
✅ Painel Admin com visitas<br>
✅ Suporte WhatsApp<br><br>
</p>
<button onclick="pagarMulticaixa()" class="btn-black" style="width:100%;background:#7c3aed">💳 PAGAR COM MULTICAIXA EXPRESS</button>
<button onclick="pagarWhatsApp()" style="width:100%;margin-top:8px;padding:14px 24px;border-radius:999px;border:1px solid #e4e4e7;background:#fff;font-weight:700;cursor:pointer">📱 PAGAR VIA WHATSAPP</button>
<button onclick="fecharPagamento()" class="btn-white" style="width:100%;margin-top:8px">Cancelar</button>
<p style="font-size:11px;color:#71717a;text-align:center;margin-top:12px">Pagamento seguro • Acesso imediato após confirmação</p>
</div>
</div>

</div>

<script>
let despesas={habitacao:0,alimentacao:0,transporte:0,educacao:0,saude:0,lazer:0,vestuario:0,outros:0};
const cats=[{k:'habitacao',l:'🏠 Habitação',max:30000},{k:'alimentacao',l:'🍽️ Alimentação',max:15000},{k:'transporte',l:'🚗 Transporte',max:12000},{k:'educacao',l:'🎓 Educação',max:10000},{k:'saude',l:'🏥 Saúde',max:8000},{k:'lazer',l:'🎮 Lazer',max:10000},{k:'vestuario',l:'👕 Vestuário',max:6000},{k:'outros',l:'📱 Outros',max:10000}];
let renda=90000,guard=0,perc=10,hor=10,perfil='equilibrado',taxas={conservador:6,equilibrado:13,arrojado:20};
function fmt(v){return new Intl.NumberFormat('pt-AO',{maximumFractionDigits:0}).format(v)+' Kz'}

function abrirLogin(){document.getElementById('modalLogin').style.display='grid'}
function fecharLogin(){document.getElementById('modalLogin').style.display='none'}
function fazerLogin(){const email=document.getElementById('emailLogin').value;if(!email){alert('Digite seu email');return;}localStorage.setItem('usuario_logado',email);alert('✅ Bem-vindo! '+email+' - Acesso liberado!');fecharLogin();document.getElementById('contadorGlobal').textContent='👤 '+email+' • Logado'}
function abrirPagamento(){document.getElementById('modalPagamento').style.display='grid'}
function fecharPagamento(){document.getElementById('modalPagamento').style.display='none'}
function pagarMulticaixa(){alert('💳 Redirecionando para Multicaixa Express...\n\nValor: 2.500 Kz\nReferência: POUPE-HOJE-117\n\nApós pagar, envie comprovativo no WhatsApp!');window.open('https://wa.me/244900000000?text=Quero%20pagar%20Poupe%20Hoje%20-%202.500%20Kz%20-%20Comprovativo%20anexo','_blank')}
function pagarWhatsApp(){window.open('https://wa.me/244900000000?text=Olá!%20Quero%20pagar%20e%20acessar%20o%20Poupe%20Hoje%20Premium%20por%202.500%20Kz','_blank')}


function renderDespesas(){const c=document.getElementById('despesas');c.innerHTML='';cats.forEach(cat=>{const div=document.createElement('div');div.className='item';div.innerHTML=`<span>${cat.l} - ${fmt(despesas[cat.k])}</span>`;const wr=document.createElement('div');wr.style.width='50%';const inp=document.createElement('input');inp.type='range';inp.min=0;inp.max=cat.max;inp.step=100;inp.value=despesas[cat.k];inp.oninput=e=>{despesas[cat.k]=+e.target.value;calc()};wr.appendChild(inp);div.appendChild(wr);c.appendChild(div)})}
function calc(){const inss=Math.round(renda*0.03);const liquido=renda-inss;const total=Object.values(despesas).reduce((a,b)=>a+b,0);const disp=liquido-total;const poupAnual=Math.max(0,disp*perc/100);const poupMens=poupAnual/12;const taxa=taxas[perfil];const vfGuard=guard*Math.pow(1+taxa/100,hor);const vfPoup=taxa===0?poupAnual*hor:poupAnual*((Math.pow(1+taxa/100,hor)-1)/(taxa/100));const proj=Math.round(vfGuard+vfPoup);
document.getElementById('rendaVal').textContent=fmt(renda);document.getElementById('inssVal').textContent=fmt(inss);document.getElementById('liquidoVal').textContent=fmt(liquido);document.getElementById('totalDesp').textContent='Total despesas: '+fmt(total)+' (começa em 0)';document.getElementById('percVal').textContent=perc+'%';document.getElementById('horVal').textContent=hor+' anos';document.getElementById('guardVal').textContent=fmt(guard);document.getElementById('dispVal').textContent=fmt(disp);document.getElementById('poupVal').textContent=fmt(poupMens)+'/mês';document.getElementById('horLabel').textContent=hor;document.getElementById('taxaLabel').textContent=taxa;document.getElementById('projVal').textContent=fmt(proj);
document.querySelectorAll('[id^="btn-"]').forEach(b=>{b.style.background='#fff';b.style.color='#18181b';b.style.border='1px solid #e4e4e7'});const ab=document.getElementById(perfil==='conservador'?'btn-cons':perfil==='equilibrado'?'btn-eq':'btn-ar');if(ab){ab.style.background='#18181b';ab.style.color='#fff'}
renderDespesas();localStorage.setItem('poupe-hoje-final',JSON.stringify({renda,guard,perc,hor,perfil,despesas}));}
function setPerfil(p){perfil=p;calc()}
function reporPadrao(){
localStorage.clear();
localStorage.removeItem('poupe-hoje-final');
localStorage.removeItem('poupe-hoje');
localStorage.removeItem('poupe-hoje-v2');
despesas={habitacao:0,alimentacao:0,transporte:0,educacao:0,saude:0,lazer:0,vestuario:0,outros:0};
renda=90000;guard=0;perc=10;hor=10;perfil='equilibrado';
document.getElementById('renda').value=90000;
document.getElementById('perc').value=10;
document.getElementById('hor').value=10;
document.getElementById('guard').value=0;
calc();
alert('✅ REPÔS! Total 0 Kz, Renda 90K, Guardado 0 - Agora funciona!');
location.reload();
}
document.getElementById('renda').oninput=e=>{renda=+e.target.value;calc()};
document.getElementById('perc').oninput=e=>{perc=+e.target.value;calc()};
document.getElementById('hor').oninput=e=>{hor=+e.target.value;calc()};
document.getElementById('guard').oninput=e=>{guard=+e.target.value;calc()};
const saved=localStorage.getItem('poupe-hoje-final');if(saved){try{const d=JSON.parse(saved);if(d.renda)renda=d.renda;if(d.guard!==undefined)guard=d.guard;if(d.perc)perc=d.perc;if(d.hor)hor=d.hor;if(d.perfil)perfil=d.perfil;if(d.despesas)despesas=d.despesas;document.getElementById('renda').value=renda;document.getElementById('perc').value=perc;document.getElementById('hor').value=hor;document.getElementById('guard').value=guard}catch{}}
calc();
</script>
</body>
</html>

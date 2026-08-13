<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="format-detection" content="telephone=no">
<title>Mi aventura del agua</title>
<style>
:root{--azul:#0878a7;--azul2:#075b80;--verde:#159b82;--bg:#eef9fd;--text:#17384b;--border:#cfe7f0}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{margin:0;padding:0;width:100%;min-height:100%;font-family:-apple-system,BlinkMacSystemFont,"Helvetica Neue",Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-text-size-adjust:100%}
body{padding-bottom:calc(28px + env(safe-area-inset-bottom))}
header{background:linear-gradient(135deg,#0878a7,#159b82);color:#fff;text-align:center;padding:calc(24px + env(safe-area-inset-top)) 16px 30px}
header h1{margin:0;font-size:34px;line-height:1.05} header p{margin:10px auto 0;max-width:650px;font-size:16px;line-height:1.4}
main{max-width:760px;margin:0 auto;padding:12px}
.status{border-radius:16px;padding:13px 14px;margin:12px 0;font-size:13px;line-height:1.4;font-weight:700;background:#fff3c7;border:2px solid #f1d36b;color:#6b5410}
.status.ok{background:#e5fbef;border-color:#8bd1aa;color:#17623a}
.card{background:#fff;border:1px solid var(--border);border-radius:20px;padding:16px;margin:12px 0;box-shadow:0 5px 18px rgba(0,80,120,.08)}
.card h2{margin:0 0 8px;color:var(--azul2);font-size:21px} .help{margin:0 0 12px;color:#607987;font-size:14px;line-height:1.4}
.grid{display:grid;grid-template-columns:1fr;gap:10px}
.item{border:1px solid #d8eaf1;border-radius:18px;background:#fbfeff;padding:12px}
.itemTop{display:flex;align-items:center;gap:10px} .icon{display:flex;align-items:center;justify-content:center;width:46px;min-width:46px;height:46px;border-radius:14px;background:#e7f7fd;font-size:28px}
.itemName{font-weight:800;font-size:15px;line-height:1.2} .itemHint{font-size:11px;color:#708592;margin-top:3px}
.controls{display:grid;grid-template-columns:64px 1fr 64px;gap:10px;align-items:center;margin-top:12px}
.tap{width:64px;height:56px;display:flex;align-items:center;justify-content:center;border-radius:16px;font-size:36px;font-weight:900;line-height:1;user-select:none;-webkit-user-select:none;position:relative;z-index:5}
.tapMinus{background:#d9eef6;color:#075b80;border:3px solid #a9d4e3}
.tapPlus{background:#0878a7;color:#fff;border:3px solid #075b80;box-shadow:0 3px 0 #064a68}
.qty{text-align:center} .qty input{width:100%;height:56px;border:2px solid #cfe3eb;border-radius:14px;background:#fff;color:#17384b;-webkit-text-fill-color:#17384b;text-align:center;font-size:20px;font-weight:850;-webkit-appearance:none;appearance:none;opacity:1}
.unit{font-size:10px;color:#708592;margin-top:4px}
.transport{display:grid;grid-template-columns:repeat(2,1fr);gap:9px}
.transportChoice{min-height:90px;display:flex;flex-direction:column;align-items:center;justify-content:center;border:2px solid #d5e9f0;border-radius:17px;background:#fff;color:#17384b;font-size:13px;font-weight:800;user-select:none;-webkit-user-select:none}
.transportChoice .emoji{font-size:30px;margin-bottom:5px} .transportChoice.active{background:#e0f6ff;border-color:#1ca4da;color:#075b80}
.bigAction{width:100%;min-height:60px;display:flex;align-items:center;justify-content:center;border-radius:18px;background:linear-gradient(135deg,#0878a7,#159b82);color:#fff;font-size:18px;font-weight:900;margin:14px 0;box-shadow:0 6px 16px rgba(8,120,167,.22);user-select:none;-webkit-user-select:none}
#results{display:none} .resultHead{background:linear-gradient(135deg,#0878a7,#159b82);color:#fff;border-radius:18px;padding:20px 12px;text-align:center}
.resultHead .label{font-size:13px;font-weight:800} .resultHead .total{font-size:54px;line-height:1;font-weight:900;margin:8px 0} .resultHead .total small{font-size:20px}
.chips{display:grid;grid-template-columns:1fr;gap:8px;margin-top:12px} .chip{background:#f4fbfe;border:1px solid #d4eaf2;border-radius:14px;padding:11px;text-align:center} .chip b{display:block;font-size:20px;color:#0878a7}
.compare{display:grid;grid-template-columns:1fr 1fr;gap:9px} .compareBox{border:1px solid #d7eaf1;border-radius:16px;padding:13px;text-align:center;background:#fff} .compareBox .ci{font-size:35px} .compareBox strong{display:block;font-size:24px;color:#0878a7;margin:4px 0} .compareBox span{font-size:12px}
.toplist{padding:0;margin:0;list-style:none} .toplist li{display:flex;justify-content:space-between;gap:10px;padding:9px 0;border-bottom:1px dashed #d6e6ed;font-size:13px}
.note{background:#fff7d9;border:1px solid #f3dfa0;border-radius:15px;padding:12px;font-size:13px;line-height:1.4}
@media(min-width:620px){.grid{grid-template-columns:1fr 1fr}.transport{grid-template-columns:repeat(3,1fr)}.chips{grid-template-columns:repeat(3,1fr)}}
@media(max-width:380px){header h1{font-size:30px}main{padding:9px}.controls{grid-template-columns:58px 1fr 58px;gap:8px}.tap{width:58px;height:54px;font-size:33px}.qty input{height:54px}.compare{grid-template-columns:1fr}}
</style>
</head>
<body>
<header>
  <h1>💧 Mi aventura del agua</h1>
  <p>Marca lo que hiciste hoy y descubre cuánta agua estuvo detrás de tu día.</p>
</header>
<main>
  <div id="status" class="status">⚠️ Si ves este mensaje amarillo, estás en una vista previa que no ejecuta la calculadora. Los controles se verán, pero para calcular debes abrir esta página desde una dirección web <b>https://</b> en Safari.</div>

  <section class="card"><h2>🚿 1. Agua que sí viste</h2><p class="help">Toca los cuadros grandes de <b>−</b> y <b>+</b>.</p><div class="grid">
    <div class="item" data-group="direct" data-factor="9.46" data-name="Me bañé" data-icon="🚿">
      <div class="itemTop">
        <div class="icon">🚿</div>
        <div class="itemText">
          <div class="itemName">Me bañé</div>
          <div class="itemHint">minutos de regadera</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_shower" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_shower" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Me bañé">
          <div class="unit">min</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_shower" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="direct" data-factor="6.06" data-name="Usé el sanitario" data-icon="🚽">
      <div class="itemTop">
        <div class="icon">🚽</div>
        <div class="itemText">
          <div class="itemName">Usé el sanitario</div>
          <div class="itemHint">número de descargas</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_wc" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_wc" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Usé el sanitario">
          <div class="unit">veces</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_wc" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="direct" data-factor="8.33" data-name="Cepillé mis dientes" data-icon="🪥">
      <div class="itemTop">
        <div class="icon">🪥</div>
        <div class="itemText">
          <div class="itemName">Cepillé mis dientes</div>
          <div class="itemHint">minutos con la llave abierta</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_teeth" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_teeth" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Cepillé mis dientes">
          <div class="unit">min</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_teeth" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="direct" data-factor="8.33" data-name="Lavé mis manos" data-icon="🧼">
      <div class="itemTop">
        <div class="icon">🧼</div>
        <div class="itemText">
          <div class="itemName">Lavé mis manos</div>
          <div class="itemHint">minutos acumulados</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_hands" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_hands" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Lavé mis manos">
          <div class="unit">min</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_hands" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="direct" data-factor="0.25" data-name="Tomé agua" data-icon="🥤">
      <div class="itemTop">
        <div class="icon">🥤</div>
        <div class="itemText">
          <div class="itemName">Tomé agua</div>
          <div class="itemHint">vasos de 250 mL</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_drink" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_drink" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Tomé agua">
          <div class="unit">vasos</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_drink" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="direct" data-factor="8" data-name="Lavamos trastes" data-icon="🍽️">
      <div class="itemTop">
        <div class="icon">🍽️</div>
        <div class="itemText">
          <div class="itemName">Lavamos trastes</div>
          <div class="itemHint">minutos con agua corriendo</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_dishes" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_dishes" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Lavamos trastes">
          <div class="unit">min</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_dishes" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div></div></section>
  <section class="card"><h2>🍽️ 2. Agua escondida en la comida</h2><p class="help">Los alimentos también necesitan agua para producirse.</p><div class="grid">
    <div class="item" data-group="virtual" data-factor="2400" data-name="Hamburguesa de res" data-icon="🍔">
      <div class="itemTop">
        <div class="icon">🍔</div>
        <div class="itemText">
          <div class="itemName">Hamburguesa de res</div>
          <div class="itemHint">1 pieza ≈ 2,400 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_burger" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_burger" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Hamburguesa de res">
          <div class="unit">piezas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_burger" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="2310" data-name="Porción de res" data-icon="🥩">
      <div class="itemTop">
        <div class="icon">🥩</div>
        <div class="itemText">
          <div class="itemName">Porción de res</div>
          <div class="itemHint">aprox. 150 g</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_beef" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_beef" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Porción de res">
          <div class="unit">porciones</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_beef" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="645" data-name="Porción de pollo" data-icon="🍗">
      <div class="itemTop">
        <div class="icon">🍗</div>
        <div class="itemText">
          <div class="itemName">Porción de pollo</div>
          <div class="itemHint">aprox. 150 g</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_chicken" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_chicken" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Porción de pollo">
          <div class="unit">porciones</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_chicken" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="250" data-name="Porción de arroz" data-icon="🍚">
      <div class="itemTop">
        <div class="icon">🍚</div>
        <div class="itemText">
          <div class="itemName">Porción de arroz</div>
          <div class="itemHint">aprox. 100 g</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_rice" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_rice" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Porción de arroz">
          <div class="unit">porciones</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_rice" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="255" data-name="Vaso de leche" data-icon="🥛">
      <div class="itemTop">
        <div class="icon">🥛</div>
        <div class="itemText">
          <div class="itemName">Vaso de leche</div>
          <div class="itemHint">250 mL</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_milk" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_milk" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Vaso de leche">
          <div class="unit">vasos</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_milk" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="196" data-name="Huevo" data-icon="🥚">
      <div class="itemTop">
        <div class="icon">🥚</div>
        <div class="itemText">
          <div class="itemName">Huevo</div>
          <div class="itemHint">1 pieza ≈ 196 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_egg" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_egg" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Huevo">
          <div class="unit">huevos</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_egg" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="40" data-name="Pan" data-icon="🍞">
      <div class="itemTop">
        <div class="icon">🍞</div>
        <div class="itemText">
          <div class="itemName">Pan</div>
          <div class="itemHint">1 rebanada ≈ 40 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_bread" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_bread" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Pan">
          <div class="unit">rebanadas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_bread" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="70" data-name="Manzana" data-icon="🍎">
      <div class="itemTop">
        <div class="icon">🍎</div>
        <div class="itemText">
          <div class="itemName">Manzana</div>
          <div class="itemHint">1 pieza ≈ 70 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_apple" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_apple" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Manzana">
          <div class="unit">piezas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_apple" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="13" data-name="Tomate" data-icon="🍅">
      <div class="itemTop">
        <div class="icon">🍅</div>
        <div class="itemText">
          <div class="itemName">Tomate</div>
          <div class="itemHint">1 pieza ≈ 13 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_tomato" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_tomato" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Tomate">
          <div class="unit">piezas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_tomato" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="253" data-name="Porción de queso" data-icon="🧀">
      <div class="itemTop">
        <div class="icon">🧀</div>
        <div class="itemText">
          <div class="itemName">Porción de queso</div>
          <div class="itemHint">aprox. 50 g</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_cheese" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_cheese" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Porción de queso">
          <div class="unit">porciones</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_cheese" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="688" data-name="Chocolate" data-icon="🍫">
      <div class="itemTop">
        <div class="icon">🍫</div>
        <div class="itemText">
          <div class="itemName">Chocolate</div>
          <div class="itemHint">aprox. 40 g</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_choc" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_choc" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Chocolate">
          <div class="unit">porciones</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_choc" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div></div></section>
  <section class="card"><h2>📱 3. Tecnología y cosas</h2><p class="help">También usamos agua indirectamente en productos y servicios.</p><div class="grid">
    <div class="item" data-group="digital" data-factor="0.0003" data-name="Usé IA de texto" data-icon="🤖">
      <div class="itemTop">
        <div class="icon">🤖</div>
        <div class="itemText">
          <div class="itemName">Usé IA de texto</div>
          <div class="itemHint">≈ 0.3 mL por consulta</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_ai" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_ai" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Usé IA de texto">
          <div class="unit">consultas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_ai" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="digital" data-factor="0.0003" data-name="Busqué en internet" data-icon="🔎">
      <div class="itemTop">
        <div class="icon">🔎</div>
        <div class="itemText">
          <div class="itemName">Busqué en internet</div>
          <div class="itemHint">estimación ilustrativa</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_search" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_search" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Busqué en internet">
          <div class="unit">búsquedas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_search" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="2495" data-name="Estrené camiseta" data-icon="👕">
      <div class="itemTop">
        <div class="icon">👕</div>
        <div class="itemText">
          <div class="itemName">Estrené camiseta</div>
          <div class="itemHint">algodón ≈ 2,495 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_shirt" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_shirt" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Estrené camiseta">
          <div class="unit">piezas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_shirt" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div>

    <div class="item" data-group="virtual" data-factor="8000" data-name="Estrené pantalón" data-icon="👖">
      <div class="itemTop">
        <div class="icon">👖</div>
        <div class="itemText">
          <div class="itemName">Estrené pantalón</div>
          <div class="itemHint">mezclilla ≈ 8,000 L</div>
        </div>
      </div>
      <div class="controls">
        <div class="tap tapMinus" role="button" tabindex="0" data-target="q_jeans" data-delta="-1" aria-label="Quitar">−</div>
        <div class="qty">
          <input id="q_jeans" type="number" min="0" step="1" value="0" inputmode="numeric" aria-label="Estrené pantalón">
          <div class="unit">piezas</div>
        </div>
        <div class="tap tapPlus" role="button" tabindex="0" data-target="q_jeans" data-delta="1" aria-label="Agregar">+</div>
      </div>
    </div></div></section>

  <section class="card">
    <h2>🚌 4. ¿Cómo viajaste?</h2><p class="help">Marca los medios que usaste. No se suman al total.</p>
    <div class="transport">
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🚶</div>Caminé</div>
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🚲</div>Bicicleta</div>
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🚌</div>Autobús</div>
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🚇</div>Metro</div>
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🚗</div>Automóvil</div>
      <div class="transportChoice" role="button" tabindex="0"><div class="emoji">🏍️</div>Moto</div>
    </div>
  </section>

  <div id="calculateBtn" class="bigAction" role="button" tabindex="0">✨ Descubrir mi huella de hoy</div>

  <section class="card" id="results">
    <div class="resultHead"><div class="label">HOY TU DÍA NECESITÓ APROXIMADAMENTE</div><div class="total"><span id="total">0</span> <small>L</small></div><div>💧 ≈ <span id="jugs">0</span> garrafones de 20 litros</div></div>
    <div class="chips"><div class="chip">🚿<b id="directR">0 L</b><span>agua directa</span></div><div class="chip">🍽️<b id="virtualR">0 L</b><span>agua escondida</span></div><div class="chip">📱<b id="digitalR">0 mL</b><span>uso digital</span></div></div>
    <h2 style="margin-top:18px">🤯 ¿A qué se parece esa cantidad?</h2><div id="comparisons" class="compare"></div>
    <h2 style="margin-top:18px">🔎 Lo que más pesó hoy</h2><ul id="toplist" class="toplist"></ul>
    <div class="note" style="margin-top:14px">🌱 <b>Reto:</b> cambia mañana una sola acción y compara tu resultado.</div>
  </section>
</main>

<script>
(function(){
"use strict";
var status=document.getElementById("status");
status.className="status ok";
status.innerHTML="✅ Calculadora activa. Los botones + y − ya pueden usarse.";

function num(n,d){try{return n.toLocaleString("es-MX",{maximumFractionDigits:d||0})}catch(e){return String(Math.round(n*10)/10)}}
function activate(el,fn){
  var touched=false;
  el.addEventListener("touchend",function(e){touched=true;e.preventDefault();fn();setTimeout(function(){touched=false},300)},{passive:false});
  el.addEventListener("click",function(e){if(touched)return;e.preventDefault();fn()});
  el.addEventListener("keydown",function(e){if(e.key==="Enter"||e.key===" "){e.preventDefault();fn()}});
}

document.querySelectorAll(".tap").forEach(function(el){
  activate(el,function(){
    var input=document.getElementById(el.getAttribute("data-target"));
    var delta=parseFloat(el.getAttribute("data-delta"))||0;
    var v=parseFloat(input.value)||0;
    input.value=Math.max(0,v+delta);
  });
});
document.querySelectorAll(".transportChoice").forEach(function(el){activate(el,function(){el.classList.toggle("active")})});

function calculate(){
  var direct=0,virt=0,dig=0,rows=[];
  document.querySelectorAll(".item").forEach(function(card){
    var input=card.querySelector("input");
    var q=parseFloat(input.value)||0;
    if(!q)return;
    var v=q*(parseFloat(card.getAttribute("data-factor"))||0);
    var g=card.getAttribute("data-group");
    if(g==="direct")direct+=v; else if(g==="virtual")virt+=v; else dig+=v;
    rows.push({icon:card.getAttribute("data-icon"),name:card.getAttribute("data-name"),v:v});
  });
  var total=direct+virt+dig;
  document.getElementById("total").textContent=num(total,total<10?1:0);
  document.getElementById("jugs").textContent=num(total/20,1);
  document.getElementById("directR").textContent=num(direct,1)+" L";
  document.getElementById("virtualR").textContent=num(virt,1)+" L";
  document.getElementById("digitalR").textContent=dig<1?num(dig*1000,1)+" mL":num(dig,1)+" L";

  var products=[["🍅","tomates",13],["🍞","rebanadas de pan",40],["🍎","manzanas",70],["🥚","huevos",196],["🥛","litros de leche",1020],["🍔","hamburguesas de res",2400],["👕","camisetas de algodón",2495],["👖","pantalones de mezclilla",8000]];
  var cw=document.getElementById("comparisons"); cw.innerHTML=""; var made=0;
  products.forEach(function(c){if(made>=4)return;var count=total/c[2];if(total>0&&count>=.2&&count<=10000){var b=document.createElement("div");b.className="compareBox";b.innerHTML='<div class="ci">'+c[0]+'</div><strong>≈ '+(count>=10?num(count,0):num(count,1))+'</strong><span>'+c[1]+'</span>';cw.appendChild(b);made++}});
  if(!made)cw.innerHTML='<div class="compareBox" style="grid-column:1/-1">Agrega algunas actividades para comparar.</div>';

  rows.sort(function(a,b){return b.v-a.v});
  var top=document.getElementById("toplist"); top.innerHTML="";
  if(!rows.length)top.innerHTML="<li><span>Sin actividades todavía</span><b>0 L</b></li>";
  else rows.slice(0,5).forEach(function(r){var li=document.createElement("li");li.innerHTML="<span>"+r.icon+" "+r.name+"</span><b>"+(r.v<1?num(r.v*1000,1)+" mL":num(r.v,0)+" L")+"</b>";top.appendChild(li)});

  var results=document.getElementById("results"); results.style.display="block";
  setTimeout(function(){try{results.scrollIntoView({behavior:"smooth",block:"start"})}catch(e){results.scrollIntoView(true)}},100);
}
activate(document.getElementById("calculateBtn"),calculate);
})();
</script>
</body>
</html>

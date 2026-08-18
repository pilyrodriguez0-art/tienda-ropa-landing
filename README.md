# Vampirx Caoticx — Landing page y campaña de Google Ads

Proyecto de e-commerce para una tienda de moda alternativa y paca curada
en Guatemala. Incluye desarrollo de landing page, automatización del
procesamiento de catálogo y configuración de campaña publicitaria.

**Sitio en vivo:** https://pilyrodriguez0-art.github.io/tienda-ropa-landing/

---

## Contexto

La tienda vendía exclusivamente por Instagram, sin sitio propio. Eso
impedía cualquier medición: no había forma de saber de dónde venían los
clientes ni de rastrear conversiones desde publicidad pagada.

El objetivo fue construir la infraestructura mínima para poder medir:
una página propia donde instalar seguimiento y a la cual dirigir tráfico.

## Qué se construyó

### Landing page
HTML y CSS sin dependencias externas. Diseño responsive con CSS Grid,
adaptado a móvil (donde ocurre la mayoría del tráfico del sector).
Alojada en GitHub Pages con HTTPS.

Decisiones de diseño:
- Paleta oscura, coherente con la identidad visual existente en Instagram
- Texto alternativo descriptivo en todas las imágenes (accesibilidad y SEO)
- Botón de contacto duplicado (inicio y cierre) para reducir fricción

### Automatización del catálogo
Script en Python para procesar las fotos de producto en lote:

- Corrección de orientación EXIF
- Redimensionado a 1200px conservando proporción
- Compresión optimizada para web

Resultado: reducción de ~3 MB a ~250 KB por imagen. El peso de la página
afecta directamente el Nivel de Calidad en Google Ads, y por lo tanto el
costo por clic.

Se evaluó también un recorte automático usando `rembg` (segmentación por
red neuronal) más `getbbox()` de Pillow. La aproximación funcionó de
forma inconsistente sobre fotografías con fondo texturizado y se descartó
en favor de recorte manual: con nueve prendas, el costo de depuración
superaba el beneficio de la automatización.

### Campaña de Google Ads
Configuración de campaña de Búsqueda:

- Investigación de palabras clave con foco en intención transaccional
  y segmentación local
- Descarte de términos amplios de alto volumen ("ropa", "bolso") que
  agotarían el presupuesto con tráfico irrelevante
- Redacción de anuncios responsivos
- Estrategia de puja: maximizar clics con límite de CPC

La elección de estrategia responde a la etapa del proyecto: las
estrategias de Smart Bidding (CPA objetivo, ROAS objetivo) requieren un
histórico de conversiones que una cuenta nueva no tiene. Configurarlas
prematuramente produce campañas que no gastan y no aprenden.

## Stack

`HTML` `CSS` `Python` `Pillow` `Git` `GitHub Pages` `Google Ads`

## Estado

Landing page publicada. Campaña configurada en borrador, pendiente de
activación y de la implementación del seguimiento de conversiones.

## Próximos pasos

- Instalar Google Tag y configurar conversión sobre el clic de contacto
- Ejecutar campaña y recopilar datos de referencia
- Migrar a Maximizar conversiones una vez alcanzado volumen suficiente

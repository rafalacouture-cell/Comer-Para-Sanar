# Comer para Sanar — Guía de alimentación para la salud digestiva

Guía web de recetas, suplementos y preparaciones para personas que conviven con gastritis y condiciones digestivas relacionadas, y que quieren comer rico, calmar la inflamación y cuidar su estómago — sin dejar de comer relativamente saludable.

## Propósito

La página está pensada para un público amplio: cualquiera que tenga gastritis (crónica o esporádica) o condiciones relacionadas y quiera comer bien sin complicarse. La gastritis es la puerta de entrada porque es la condición más común, pero el enfoque alimenticio también ayuda en casos relacionados:

- **Gastritis crónica** — reduce la inflamación y la irritación de la mucosa
- **Esófago de Barrett** — cuida el reflujo y protege el esófago
- **Atrofia gástrica** — apoya la regeneración del epitelio
- **H. pylori** — incluye alimentos que ayudan a controlar la bacteria

No es una dieta restrictiva ni clínica: es **comida deliciosa, moderna y reconfortante** que además cuida el estómago. El tono es de blog de cocina saludable aspiracional — recetas que cualquiera querría cocinar, no una lista de restricciones.

**Posicionamiento clave (IMPORTANTE):** la página NO debe leerse como "comida de enfermo" ni "dieta súper sana aburrida". Debe sentirse como comida rica que da ganas de hacer, y lo terapéutico es un bonus. Por eso:
- Las descripciones usan lenguaje apetitoso (cremoso, dorado, reconfortante, antojable), no clínico (mucosa, irritante, tolerado).
- Hay recetas indulgentes-pero-sanas: pancakes de avena, pizza de base de pollo, mousse de cacao y aguacate, nice cream de banano, bowls coloridos.
- El hero lidera con "comer rico, sentirte bien", no con el diagnóstico.

## Lógica nutricional (mantenerla en recetas nuevas)

Todas las recetas siguen el mismo criterio:
- **Proteína limpia** (pollo, pescado blanco, claras, yogur griego, proteína vegetal)
- **Carbohidratos suaves** (arroz blanco, papa, avena, quinoa lavada)
- **Vegetales no irritantes** (calabacín, zanahoria, espinaca, brócoli con moderación)
- **Sin irritantes:** nada de picante, ácido, frituras, café, alcohol, pimienta, ajo crudo
- **Proteína vegetal sobre whey** (el whey puede irritar la mucosa inflamada)
- **Compuestos con evidencia:** sulforafano (brócoli), papaína (papaya), probióticos (yogur griego)
- Cenas ligeras, idealmente unas horas antes de dormir (ayuda con el reflujo)
- Líquidos tibios, nunca muy calientes (los muy calientes irritan el esófago)

Cada receta tiene una **calificación de 1 a 10** según qué tan apropiada es para un estómago sensible. Solo se incluyen recetas con calificación >=8.5.

Las recetas son saludables de base, así que también sirven a quien simplemente quiere comer bien. Cuando hay un dato útil para quienes hacen ejercicio, se menciona de forma opcional ("si entrenas..."), sin asumir que todos lo hacen.

## Estructura de archivos

```
comer-para-sanar/
├── index.html      # La página (diseño + lógica de render)
├── datos.json      # TODO el contenido: recetas, suplementos, preparaciones
└── README.md       # Este archivo
```

**Separación clave:** el diseño vive en `index.html`, el contenido vive en `datos.json`. Para agregar/editar recetas, se edita `datos.json` — la página se actualiza sola.

> NOTA: actualmente `index.html` tiene el contenido "quemado" (hardcoded) en el HTML. La **primera tarea pendiente** es refactorizar `index.html` para que lea dinámicamente desde `datos.json` con JavaScript (fetch). Así se podrá editar solo el JSON.

## Estructura de datos.json

```json
{
  "meta": { "title", "subtitle", "conditions": [] },
  "recipes": [
    {
      "category": "desayunos|almuerzos|cenas|snacks",
      "title": "...",
      "image": "URL de la foto",
      "rating": "9/10",
      "rating_fill": 90,
      "description": "...",
      "macros": { "protein": 42, "carbs": 38, "fat": 6, "calories": 380 },
      "ingredients": ["..."],
      "steps": [ { "text": "...", "timer_seconds": 240 } ],
      "note": "tip con emoji"
    }
  ],
  "supplements": [
    { "icon": "...", "name", "rating", "rating_fill", "description", "tags": [] }
  ],
  "preparations": [
    { "title", "subtitle", "sections": [{ "title", "items": [] }], "benefit" }
  ]
}
```

## Diseño visual (mantener consistencia)

- **Estética:** cálida, orgánica, natural. Evoca un libro de cocina de autor.
- **Paleta:** sage verde `#5C7A5E`, lino `#F0EBE0`, tierra `#C4A882`, blanco roto `#FAFAF7`
- **Tipografía:** Playfair Display (títulos), Inter (cuerpo)
- **Calificación:** termómetro vertical verde (no estrellas)
- **Macros:** barra de proporción a color (verde proteína, dorado carbos, terracota grasa) + tarjetas con gramos. Calorías destacadas en grande.
- **Navegación:** 3 pestañas (Alimentación, Suplementación, Preparaciones). Dentro de Alimentación, filtros por tipo de comida.

## Estado de las fotos (PENDIENTE IMPORTANTE)

Las fotos actuales son URLs de Unsplash que **probablemente NO cargan todas** — fueron asignadas sin poder verificarlas en el entorno donde se creó esto. Dos caminos:
1. **Reemplazarlas con URLs verificadas** (Claude Code SI puede acceder a internet y comprobar que carguen).
2. **Fotos propias** — la mejor opción a largo plazo: fotos reales de cada plato.

Cuando Claude Code tenga acceso, conviene **verificar cada URL de imagen** y reemplazar las rotas.

## Tareas pendientes (en orden de prioridad)

1. **Refactorizar `index.html`** para que lea de `datos.json` dinámicamente (fetch + render con JS). Hoy está hardcoded.
2. **Verificar y arreglar las fotos** — comprobar qué URLs cargan, reemplazar las rotas.
3. **Publicar en GitHub Pages** — crear repo, subir, activar Pages, obtener URL pública.
4. **(Opcional) Panel de edición** — una forma simple de agregar recetas sin tocar el JSON a mano.

## Objetivo de publicación

GitHub Pages: hosting gratis, URL pública tipo `usuario.github.io/comer-para-sanar`. Se busca poder:
- Editar el contenido fácilmente (directo en el JSON desde la web de GitHub)
- Pedirle a Claude bloques nuevos de receta para pegar
- Que los cambios se reflejen rápido

## Disclaimer (mantener visible en la página)

La guía no reemplaza diagnóstico ni tratamiento médico. Es un complemento informado al seguimiento con un profesional de salud. Ante síntomas persistentes, consultar siempre a un médico.

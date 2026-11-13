# Bitácora · Rueda Nocturna

## Reglas del kit (MiniReto 4)
- **Radios:** `rounded-lg` para botones, campos y alertas; `rounded-2xl` para cards y paneles; `rounded-full` para etiquetas.
- **Espaciado:** escala de Tailwind en pasos de 4 y 6 (`p-4`, `p-6`, `gap-4`, `gap-6`, `space-y-8`).
- **Colores:** los seis de la marca (`ruta`, `pedal`, `noche`, `crema`, `asfalto`, `farol`). Las cards claras usan blanco (`bg-white`) como excepción.
- **Sombras:** `shadow-md` en reposo; `shadow-2xl` al pasar el mouse.
- **Foco:** `focus:ring-4` con `ring-farol` en campos y botones.

## MiniReto 1 · Prototipo con Play CDN
**Botón con Bootstrap (semana 2):** [describe con tus palabras cómo usaste `btn btn-primary` en la semana 2].
**Botón con Tailwind (hoy):** un `<a>` con utilidades sueltas: `inline-block`, `rounded-lg`, `bg-pedal`, `px-6`, `py-3`, `font-semibold`, `text-noche`, `hover:bg-farol`.
**Diferencia clave:** Bootstrap es un framework de componentes: entrega piezas terminadas (`btn`, `card`, `navbar`) y tú las adaptas. Tailwind es utility-first: entrega clases pequeñas de una sola propiedad y tú armas el componente. Bootstrap llega más rápido a algo presentable; Tailwind da más control, pero el HTML tiene más clases.
**Tiempo real:** ___ min

## MiniReto 2 · CLI y botones
- **Instalación:** `npm install -D tailwindcss @tailwindcss/cli`. Archivo `src/input.css` con `@import "tailwindcss";`. `.gitignore` con `node_modules/`.
- **Clase usada vs. no usada:** `rounded-lg` aparece en `output.css` porque está en el HTML. `bg-pink-500` no aparece porque ningún archivo escaneado la usa. La CLI solo genera las clases que encuentra en el proyecto, por eso el archivo es pequeño.
- **Variantes:** `hover:` y `focus-visible:` con `ring-4`, `ring-farol` y `ring-offset-2`. Los tres botones están en `@layer components`.
- **Teclado:** [anota qué pasó al recorrer con Tab: el anillo debe verse en cada botón].
- **Tiempo real:** ___ min

## MiniReto 3 · Cards de rutas
- Las tres cards comparten las mismas clases base. Solo cambian la imagen, el nivel, los datos y el precio.
- **Nivel por color y texto:** fácil (verde, `bg-ruta`), medio (amarillo, `bg-farol`), difícil (oscuro con anillo, `bg-noche`). El texto dice el nivel, así no depende solo del color.
- **Hover sin mover el contenido:** cambia `border` y `shadow`, no `transform`.
- **Tiempo real:** ___ min

## MiniReto 4 · Kit de componentes
- Componentes en `componentes.html`: tres botones, una card, tres alertas (`role="status"` en éxito con texto oculto "Aviso de éxito", `role="alert"` en advertencia) y dos campos con `<label for>` y `aria-describedby`.
- **Pendiente:** verificar en GitHub Pages que `output.css` carga sin 404.

## MiniReto 5 · Maquetación de la landing
- **Estructura:** `<header>`, `<main>` con secciones con `id`, y `<footer>`.
- **Contenedor:** todas las secciones usan `mx-auto max-w-6xl px-4 sm:px-6 lg:px-8`.
- **Encabezado:** `flex` con logo, enlaces y botón.
- **Rutas:** `grid grid-cols-3` desde lg. **Pasos:** `grid` de 4 columnas, porque es una cuadrícula de dos dimensiones con elementos del mismo tamaño. Con `flex` funcionaría también, pero el reparto en columnas iguales se resuelve mejor con grid.
- **Pie:** tres bloques con `flex md:justify-between`.
- **Tiempo real:** ___ min

## MiniReto 6 · Responsive
Se diseñó en mobile-first: sin prefijo para celular, `sm:` y `md:` para pantallas más grandes.

| Ancho | Qué debe verse | Resultado |
|---|---|---|
| 360 px | Encabezado apilado, nav oculto, una columna | [ ] |
| 768 px | Encabezado en fila, rutas en 2 columnas | [ ] |
| 1024 px | Rutas en 3 columnas, pasos en 4 | [ ] |
| 1280 px | Igual que 1024 px con más aire | [ ] |

**Qué se rompía antes (para llenar):** [anota lo que viste a 360 px en la landing antes de ajustar].

## MiniReto 7 · Marca y modo oscuro
**Colores de marca:** `ruta #1E7A4F`, `pedal #F39A2B`, `noche #14213D`, `crema #FAF6EF`, `asfalto #5B6470`, `farol #FFD166`.
**Fuentes:** Montserrat (títulos) y Open Sans (texto), cargadas desde Google Fonts.

**Contraste estimado** (calculado a partir de la luminancia relativa; verifícalo con el verificador WCAG antes de entregar):

| Combinación | Ratio | Cumple 4.5:1 |
|---|---|---|
| Crema sobre noche | ~15 : 1 | Sí |
| Farol sobre noche | ~11 : 1 | Sí |
| Pedal sobre noche | ~7,2 : 1 | Sí |
| Blanco sobre ruta | ~5,3 : 1 | Sí |
| Ruta sobre crema | ~5,0 : 1 | Sí |
| Asfalto sobre crema | ~5,7 : 1 | Sí |
| **Ruta sobre noche** | **~3,0 : 1** | **No** |
| **Asfalto sobre noche** | **~2,7 : 1** | **No** |

**Corrección aplicada:** en modo oscuro los precios y acentos usan `text-farol` en lugar de `text-ruta`, y los textos secundarios usan `text-crema/70` o `/80` en lugar de `text-asfalto`.

**Modo oscuro:** se activa con la preferencia del sistema (la variante `dark:` de Tailwind v4 usa `prefers-color-scheme` por defecto).
**Pendiente:** [prueba en DevTools → Rendering → prefers-color-scheme: dark y anota lo que viste].

## MiniReto 8 · Código legible y veredicto
- **Clases con `@apply`:** 3 (`btn-principal`, `btn-secundario`, `btn-contorno`). Los botones de la landing las usan.
- **Clases repetidas:** la clase más repetida es la del campo de formulario (`rounded-lg border border-asfalto bg-white px-4 py-3 text-noche focus:outline-none focus:ring-4 focus:ring-farol`), que aparece 6 veces en `index.html`. El brief limita a 3 clases con `@apply`, así que se deja repetida.
- **Orden de clases:** layout → espaciado → tipografía → color → estados.
- **Tamaño del CSS minificado:** [ejecuta `npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --minify` y anota el tamaño en el explorador de archivos].
- **Bootstrap (sitio v2.0):** [anota el tamaño del CSS y del JS que carga Bootstrap en DevTools → Network].

**Comparativa**

| Criterio | Bootstrap | Tailwind |
|---|---|---|
| Curva de aprendizaje | [tu experiencia] | Más clases que memorizar, pero cada una hace una sola cosa |
| Personalización | Se sobrescriben variables y clases | Se cambia el tema en `@theme` |
| Tamaño final | [medición] | [medición] |
| Casos de uso | Prototipos rápidos y sitios con componentes estándar | Diseños propios y marcas con identidad fuerte |

**Recomendación para Rueda Libre:** [completa con tus datos]. Con la identidad propia y el tema de marca de esta campaña, Tailwind se ajusta mejor. Para el sitio v2.0, Bootstrap puede seguir si el cliente prioriza velocidad sobre diseño propio.

## MiniReto 9 · Contrarreloj 1: inscripción
- **Controles por dato:** nombre (`text`), correo (`email`), celular (`tel`), ruta (`select`), día (`radio`), acompañantes (`number`, 0 a 3), nivel (`radio`), bici propia (`radio`), condiciones (`checkbox`).
- **Validación nativa:** `required`, `minlength="3"`, `pattern="3[0-9]{9}"` con `title`, `min`/`max`.
- **Agrupación:** cuatro `<fieldset>` con `<legend>`.
- **Tiempo real:** ___ min (cronómetro de 40 min)
- **Pendiente:** [prueba vacío, con datos inválidos y completo, solo con teclado].

## MiniReto 10 · Un solo ecosistema
- **Hecho en la landing:** el logo lleva a `../rueda-libre/index.html`; el botón "Reserva tu bici" lleva a `../rueda-libre/paginas/reservas.html`; el pie tiene enlaces al sitio y a sus páginas.
- **No hecho en Rueda Libre:** agregar "Rueda Nocturna" a la navbar y el carrusel del sitio. Se dejó sin tocar porque Rueda Libre ya está terminado.
- **Marca:** los colores de `--color-*` coinciden con las variables de `styles.css` de Rueda Libre.
- **Tiempo real:** ___ min (cronómetro de 40 min)

## MiniReto 11 · Requerimiento de última hora
- Sección de planes con `grid-cols-1` en celular y `lg:grid-cols-3` en escritorio.
- Cards con `flex flex-col` y `flex-1` en la lista, así el botón queda siempre al final.
- Pareja con `border-4 border-pedal`, `bg-farol/20`, etiqueta "Más elegido" con posición absoluta (no mueve las demás cards) y `shadow-xl`.
- **Verificación con DevTools (Computed):** [anota el ancho y el padding de las tres cards].
- **Tiempo real:** ___ min (cronómetro de 45 min)

## MiniReto 12 · Lanzamiento
**Lista de verificación**
- [ ] Estructura semántica (`header`, `main`, `section` con `id`, `footer`)
- [ ] Texto alternativo en las imágenes
- [ ] Contraste verificado (ver MiniReto 7)
- [ ] Formularios validados
- [ ] Responsive a 360, 768 y 1280 px
- [ ] Modo claro y oscuro
- [ ] Cero 404 en GitHub Pages
- [ ] Sin estilos en línea (`style=""`) ni `<style>`
- [ ] Validador W3C sin errores: [resultado]

**Pendiente:** capturas de escritorio, celular y modo oscuro; URL de GitHub Pages; demo de tres minutos.

## Plan de commits
1. `feat: prototipo con Play CDN` (MiniReto 1)
2. `feat: proyecto Tailwind CLI y botones` (MiniReto 2)
3. `feat: cards de rutas` (MiniReto 3)
4. `feat: kit de componentes` (MiniReto 4)
5. `feat: layout de la landing` (MiniReto 5)
6. `feat: diseño responsive` (MiniReto 6)
7. `feat: tema de marca y modo oscuro` (MiniReto 7)
8. `refactor: @apply y minificado` (MiniReto 8)
9. `feat: formulario de inscripción` (MiniReto 9)
10. `feat: integración con Rueda Libre` (MiniReto 10)
11. `feat: sección de planes` (MiniReto 11)
12. `release: Rueda Nocturna v1.0` (MiniReto 12)

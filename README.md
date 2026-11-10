# Capacidad 2028 · Simulador

Simulador de la Clase 7 «De Skill a Portfolio» del programa Learning Design (UdeSA Educación Ejecutiva, 2026). Cada grupo decide, con presupuesto y horas limitados, cómo desarrollar un rol de Banco Aleph (caso ficticio) que la IA está transformando. El tablero docente muestra en vivo los portfolios de todos los grupos.

## Archivos

- `index.html`: la herramienta completa (vista de grupo y vista docente).
- `Code.gs`: backend en Google Apps Script que guarda los resultados en Google Sheets.

## 1. Conectar la planilla (Google Apps Script)

1. Crear una planilla nueva en Google Drive.
2. En la planilla: **Extensiones > Apps Script**. Borrar el contenido, pegar `Code.gs` y guardar.
3. **Implementar > Nueva implementación**. Tipo: **Aplicación web**. Ejecutar como: **Yo**. Quién tiene acceso: **Cualquier persona**.
4. Autorizar los permisos y copiar la URL que termina en `/exec`.
5. Abrirla en el navegador: tiene que mostrar `{"ok":true,"info":"Capacidad 2028 · backend activo"}`.

Si después se modifica `Code.gs`, hay que publicar una versión nueva (**Implementar > Administrar implementaciones > Editar > Nueva versión**); la URL se mantiene.

## 2. Configurar la herramienta

En `index.html`, al comienzo del script:

```js
const CONFIG = {
  endpoint: 'PEGAR AQUÍ LA URL /exec',
  clase: 'LD2026-C7'
};
```

`clase` separa los resultados de cada edición o cohorte: cambiarlo para una cohorte nueva evita mezclar datos en la misma planilla.

## 3. Publicar en GitHub Pages

1. Subir `index.html` al repositorio (en la raíz o en una carpeta, por ejemplo `clase7/`).
2. **Settings > Pages > Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Enlaces:
   - Grupos: `https://<usuario>.github.io/<repo>/` (o `/clase7/`)
   - Docente: el mismo enlace con `#docente` al final.

## En clase

- Una persona por sala comparte pantalla y abre el enlace de grupos.
- Al terminar, cada grupo toca **Guardar**: su portfolio aparece en el tablero docente (se actualiza cada 5 segundos).
- Si algo falla, el grupo pega en el chat el código que empieza con `C28-`, y en el tablero docente se pega en «Pegar códigos del chat».
- El avance de cada grupo queda guardado en el navegador de quien comparte pantalla.

## Privacidad

La planilla guarda solo lo que escriben los grupos: sala, nombre de grupo opcional, decisiones y reflexiones. No pide nombres ni correos. Conviene recordarles que no escriban datos personales en los campos de texto.

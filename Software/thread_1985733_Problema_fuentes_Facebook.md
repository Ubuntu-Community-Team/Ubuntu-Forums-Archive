---
title: "Problema fuentes Facebook"
date: 2012-05-23
forum: Software
---

### Post by dienavarrete on 2012-05-23
Buenas gente, como soy nuevo me presento, me llamo Diego Navarrete, vivo en el Conurbano, más precisamente en La Matanza y estudio Ingeniería en informática y ya soy Técnico de la misma especialidad.

Ya llevo bastante tiempo usando Ubuntu, no soy ningún experto pero creo que me manejo bastante bien, y mi problema es el siguiente:

instalé la última versión de Ubuntu, la 12.04 y Facebook se veía con su fuente tipográfica, pero después instalé Google Maps, que tuve problema con las fuentes, investigando por la web, instalé un paquete que se llama "mscorefonts" o algo de ese estilo, el problema de Google Earth no me lo solucionó y Facebook se vé mal, aunque desinstale ese paquete, así que recurro a ustedes para ver si me pueden dar una manito. Muchas gracias.. :KS

---

### Post by papibe on 2012-05-23
Hola dienavarrete. Bienvenido a los foros!

Una alternativa es usar las versiones libres de esos fonts: ttf-liberation.

Si eso no funciona, trata instalar el siguiente paquete:
```
sudo apt-get install ubuntu-restricted-extras
```
Eso incluye los mismos fonts que instalaste antes pero además incluye otros scripts para actualizarlos adecuadamente.

Espero que esto te sirve y cuéntanos como te va.
Saludos.

Referencias: [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") y [MS Fonts]("https://help.ubuntu.com/community/RestrictedFormats/Microsoft_Fonts").

---

### Post by dienavarrete on 2012-05-23
Muchas gracias, desinstale el paquete "mscorefonts" y mediante synaptic reinstale "ubuntu-restricted-extras" y ahora se ve como antes. Muchas gracias por la solución rápida.. :guitar:

---

### Post by papibe on 2012-05-23
:D Súper!

Por favor marca la conversación como resuelta ([solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")). De esa manera otras personas pueden llegar más rápido a la solución en un problema silimar.

Saludos.

EDIT: parece que ya lo hiciste, perdón por la insistencia.

---


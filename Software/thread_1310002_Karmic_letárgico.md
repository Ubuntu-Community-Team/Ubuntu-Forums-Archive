---
title: "Karmic letárgico"
date: 2009-11-01
forum: Software
---

### Post by nemodot on 2009-11-01
Encuentro muy bonito y rápido al iniciar y apagar a la nueva versión de ubuntu pero tengo un problema muy irritante.

Sucede que esta muy colgado de a ratos. 
Lo peor es que el puntero del mouse se queda congelado unos instantes mientras lo desplazo por la pantalla y todo se comporta como si estuviera jugando a 5 *frames per second*

Aún asi no parece haber un gran consumo de memoria (200 mb cuando tengo 1Gb disponible) y la pc no hace el típico ruido que hace cuando esta verdaderamente a full, como cuando usaba windows.

No sé de que se trata, maté algunos procesos sin éxito, desactive compiz pero nada funciona.

---

### Post by josecuervo86 on 2009-11-01
podrias correr ```
glxgears
``` en consola para ver cuantos frames por segundo esta tirando?

---

### Post by emiliano_raso on 2009-11-02
200MB de Ram?
Me parece mucho, yo tambien tengo 1GB y solo me consume entre 80 y 100.

---

### Post by nemodot on 2009-11-02
Parece ser que el problema se terminó cuando elimine la última versión del controlador de nvidia e instale la anterior. 

[IMG]http://imgur.com/B8XR4l.png[/IMG]

---


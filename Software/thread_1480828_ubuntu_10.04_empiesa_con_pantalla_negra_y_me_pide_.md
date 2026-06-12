---
title: "ubuntu 10.04 empiesa con pantalla negra y me pide usuario."
date: 2010-05-12
forum: Software
---

### Post by muuerto on 2010-05-12
Prendo mi computadora y me sale una pantalla negra que me pide  usuario y contraseña, las pongo y sale el terminal, y no se puede hacer  nada, busque en internet (desde otro pc) y decia que pusiera control +  alt + F4, sale una pantalla y dice que esta checkando unas cosas.. aca  una foto
 [http://img266.imageshack.us/img266/876/image00213d.jpg](http://img266.imageshack.us/img266/876/image00213d.jpg)
 y reinicie y prendio, pero sucede siempre ahora, ademas el panel de  arriba esta fallando
aca una foto...
 [http://img404.imageshack.us/img404/9022/pantallazom.png](http://img404.imageshack.us/img404/9022/pantallazom.png)
(arriba a la derecha)
 que me recomiendan hacer ?
 gracias

---

### Post by bichopro on 2010-05-13
supongo que tu tarjeta es nvidia y tiene problema con plymouth, te recomiendo pruebes con esto:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

lo del panel quizas venga por lo mismo, como supongo que en algun momento partio con menor resolucion los iconos de descuadraron por asi decirlo. si arreglas lo del inicio y esto otro no se soluciona prueba con esto:

> Resetear el escritorio es sencillo, basta con acceder al directorio $HOME del usuario. y borrar los siguientes archivos ocultos: .gnome, .gnome2, .gconf, .gconfd, .metacity. Luego nos desconectamos. De esta manera el escritorio se resetea y la próxima vez que hagamos login estará como nuevo.

---

### Post by RafaelG on 2010-09-09
Muuerto,

Por favor, la próxima vez que desees publicar una duda en el foro  te pido que lo hagas en el subforo adecuado. Si no tienes muy clara la  división que utilizamos puedes leer el siguiente post:
[http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475)

También te pido que leas las normas que intentamos aplicar en el foro para que tu experiencia en el mismo sea más efectiva:
[http://ubuntuforums.org/showthread.php?t=1162750](http://ubuntuforums.org/showthread.php?t=1162750)

Saludos!

---


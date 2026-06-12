---
title: "script de copia de archivos"
date: 2009-10-15
forum: Software
---

### Post by capcabgue on 2009-10-15
Hola a todos, llevo un tiempo utilizando ubuntu, pero rpimera vez que quiero hacer un script (y aprendí que son).

Bueno, la idea es la siguiente, recibo todos los días 18 archivos *.txt y cada archivo esta constituido por 1000 filas y 6 columnas. Lo que yo necesito es crear una solo archivo que junte todos los txt y le borre las primeras 14 filas de cada uno y la primera columna del nuevo archivo creado. en los datos que me envían son creados en distintos días por lo cual debo separarlos por días de creación.
Lo que hasta la fecha tengo es juntar los txt en un solo archivo y borrado las 14 primeras líneas de cada archivo que uní, lo anterior con el siguiente script:

#! /usr/bin/ksh
##
file='ls *TXT'
for f in $file ; do
tail +14 $f >> /SYSTEM/TRANSFERTS/GC/APF_Result
done

Alguien me puede ayudar??

Gracias

---

### Post by moreback on 2009-10-15
Hola, veo que llevas bastante tiempo en el foro así que por favor trata de respetar las reglas y publicar donde corresponde.

Este foro principal no es para publicar preguntas, la tuya debiera ir en Software.

Saludos.

---

### Post by capcabgue on 2009-10-15
Sorry, la verdad pensé que como decía software era para instalación o desinstalación de SW que existen o que se quieran agragar a nuestro querido ubuntu.
Esto como era de desarrollo, no creí que era SW.

En todo caso, no se va a volver a repetir (espero)

---

### Post by Patriciologico on 2009-10-16
Hola Capcabgue, 

 Muevo tu post ;) en Software agregamos todo lo que se puede insultar y no patear :p

Saludos!

---


---
title: "[Modificando el escritorio]Cambiar iconos solo de las carpetas"
date: 2009-06-25
forum: Software
---

### Post by rubioo on 2009-06-25
Hello !

 Bueno, estoy en plena modificación de mi escritorio :P
 Y la verdad que me gustan los iconos que tengo, salvo por los de las 
 carpetas que me parecen muy feos.
 Por eso posteo para preguntar si se pueden cambiar todos los iconos de las
 carpetas (pero solo de las carpetas).
 Porque para cambiarlos entrando a propiedades y desde ahi elegir el icono
 voy a estar bastante tiempo, si tengo que hacerlo en cada carpeta...
 

          Saludos y Gracias :D

---

### Post by staar on 2009-06-25
sip, pero vas a tener que modificar el pack de íconos...
lo primero es ir hasta la carpeta del pack de íconos, puede ser /usr/share/icons/*nombredeltema* (si está instalado para todo el sistema) o /home/*usuario*/.icons/*nombredeltema*, y fijarte que tamaños de ícono trae el pack (generalmente 128x128, 64x64, 48x48, 32x32, 24x24, y 16x16), después redimensionas una copia del ícono que querés poner a todos esos tamaños, y los vas poniendo en la carpeta del tamaño respectivo, dentro de la subcarpeta places, con el nombre folder.png (obviamente sustituyendo el ícono original), al final recargas el pack (aplicando otro y volviendo), y listo...

saludos

---

### Post by rubioo on 2009-06-25
Gracias staar, entonces por ahi me emociono y me hago mi propio pack de
 iconos :D

 Edit:
 Los iconos que quiero que sean para mis carpetas no traen (128x128, 64x64, 48x48....) pero mi tema actual (el que me gusta todo menos los 
 iconos de las carpetas si). Donde los pongo? en que carpeta?

            Saludos

---

### Post by staar on 2009-06-25
agarrá el ícono más grande y redimensioná copias con el gimp a los otros tamaños, el ícono de las carpetas está en *nombredelpack*/*tamaño*/places/folder.png (tienen que tener ese nombre, y sobreescribir al que esté, obviamente)...

por ejemplo, me gusta el pack Eikon y quiero cambiarle el ícono de carpeta por uno que tengo que se llama folder.png, lo que yo hago es empezar por el más grande, creo una carpeta con el nombre 128x128, y dentro de ella, otra con el nombre places, y dentro de esta última copio el folder.png, después hago copias de la carpeta 128x128 cambiándoles el nombre por los diferentes tamaños que tiene el pack, después abro con el gimp (o algún programa que permita redimensionar imágenes, y lo haga bien) cada uno de los diferentes archivos folder.png que están en esas carpetas, y los redimensiono adecuadamente, finalmente, selecciono todas las carpetas (128x128, 64x64, 48x48, etc) y las copio al directorio del pack de íconos, dándole para que sobrescriba los archivos, luego recargo el pack, y listo, ya tengo los íconos cambiados...

guarda que hacer un pack es medio bardo, hay que hacer muchos enlaces simbólicos a íconos, porque algunos programas buscan el mismo ícono pero con otro nombre...

saludos

---


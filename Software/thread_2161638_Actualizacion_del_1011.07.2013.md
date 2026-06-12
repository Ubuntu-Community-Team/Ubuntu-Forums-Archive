---
title: "Actualizacion del 10/11.07.2013"
date: 2013-07-11
forum: Software
---

### Post by mecdem on 2013-07-11
Hola.

El navegador es Firefox 22.0
Sobre Ubuntu 12.04

Anoche hubo una actualización de software y hoy encuentro problemas:

Ver imágenes en [https://plus.google.com/photos/100997509458764722861/albums/5899373313832334337?banner=pwa&authkey=CJ3LjumD9oP8MA](https://plus.google.com/photos/100997509458764722861/albums/5899373313832334337?banner=pwa&authkey=CJ3LjumD9oP8MA)

No supe poner nombre a las imágenes.
Las dos primeras son de páginas al azar.
La tercera es de mi blog ([http://elblogdemec.blogspot.com.ar/](http://elblogdemec.blogspot.com.ar/))
La cuarta es de un sitio de juegos que hasta anoche funcionaban.
La quinta es de YouTube.

Posteo en este foro porque parecería un fallo de la actualización.

Gracias anticipadas por la atención del tema.
Saludos.

---

### Post by mecdem on 2013-07-11
> Ver imágenes en [https://plus.google.com/photos/100997509458764722861/albums/5899373313832334337?banner=pwa&authkey=CJ3LjumD9oP8MA](https://plus.google.com/photos/100997509458764722861/albums/5899373313832334337?banner=pwa&authkey=CJ3LjumD9oP8MA)

Acabo de agregar una imagen del informe que la actualización de anoche produjo al finalizar. Al releerlo me ha parecido que podría tener que ver con este problema.

A partir de lo que dice el informe, he buscado con Synaptic el flashplugin-installer, que aparece instalado en su versión 11.2.202.297ubuntu0.12.04.1

---

### Post by gmunioz on 2013-07-11
Prueba con:
> sudo su
apt-get update
apt-get install --reinstall flashplugin-installer


---

### Post by gmunioz on 2013-07-11
Duplicado

---

### Post by mecdem on 2013-07-11
Hola gmunioz. Gracias por tu ayuda.

Seguí tus indicaciones, pero me parece que la instrucción
> apt-get install --reinstall flashplugin-installer
ha tenido un comportamiento anómalo.
(Perdona si digo un disparate informático. Soy una usuaria 'no informática')

Pongo aquí el resultado de esa línea:

root@HAL9003:/home/mecdem# apt-get install --reinstall flashplugin-installer
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 1 reinstalados, 0 para eliminar y 15 no actualizados.
Se necesita descargar 0 B/6.932 B de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
Preconfigurando paquetes ...
(Leyendo la base de datos ... 231859 ficheros o directorios instalados actualmente.)
Preparando para reemplazar flashplugin-installer 11.2.202.297ubuntu0.12.04.1 (usando .../flashplugin-installer_11.2.202.297ubuntu0.12.04.1_i386.deb) ...
Desempaquetando el reemplazo de flashplugin-installer ...
Procesando disparadores para update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.297.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.297.orig.tar.gz)
[I](NOTA: AQUÍ EL PROCESO SE DETUVO UN BUEN RATO, EL PROMPT DEJO DE TITILAR.
Pulsé alguna tecla que puso unos signos, los borré con backspace, y el proceso continuó
con lo que sigue)[/I]
Installing from local file /tmp/tmp0j2Gxg.gz
Flash Plugin installed.
Configurando flashplugin-installer (11.2.202.297ubuntu0.12.04.1) ...
root@HAL9003:/home/mecdem# 

Aparentemente estaría terminado. Si pulso flecha abajo aparece la última instrucción.

Pero si intento cerrar la terminal aparece este mensaje:

¿Cerrar esta terminal?
Aun hay un proceso ejecutándose en esta terminal. Cerrar la terminal lo matará.
Cancelar - Cerrar la terminal

De momento no me he animado a cerrar la terminal, a la espera de tu siguiente instrucción que desde ya agradezco.

---

### Post by mecdem on 2013-07-11
> ...me parece que la instrucción ha tenido un comportamiento anómalo...

...y obnubilada por ese parecer, omití hacer *lo único inteligente* que correspondía hacer antes de ponerte toda esa parrafada del post anterior: ir a ver si el problema se había solucionado o no.

**_¡¡Y sí!! ¡¡Ahora se ve todo perfecto!!_**

Agradezco tu ayuda.
Y si tienes un minuto más, cuéntame qué podría haber estado ocurriendo que la terminal tiraba ese mensaje.
Siempre y cuando explicármelo no te lleve más de un minuto.

Nuevamente, mil gracias.

---

### Post by gmunioz on 2013-07-12
Hola mecdem: que ocurrió exactamente no sé. Puede ser que el mensaje se haya debido a que estabas trabajando como usuaria con permisos temporarios de administrador, eso lo haces con la orden sudo su, ante otro mensaje como el que te apareció prueba ejecutar exit, para luego cerrar la terminal. El tiempo que quedó aparentemente en espera, fue el tiempo que llevó descargar el archivo .tar.gz del sitio de Canonical, para luego descomprimirlo e instalarlo.

---

### Post by mecdem on 2013-07-13
Gabriel, no solo me has ayudado sino que además me has ilustrado.
Muchísimas gracias.

(Jamás recuerdo cómo se pone el SOLVED. ¿Lo puedes poner? Gracias)

---


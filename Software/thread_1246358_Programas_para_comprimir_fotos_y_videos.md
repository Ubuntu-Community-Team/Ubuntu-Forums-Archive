---
title: "Programas para comprimir fotos y videos???"
date: 2009-08-21
forum: Software
---

### Post by ivisdrek on 2009-08-21
Hola a todos, me preguntaba si podían recomendarme algún programa para comprimir fotos y vídeos. En Windows manejo el JPG Rezise para fotos y el Free Vídeo Converter, son muy fáciles e intuitivos de usar. ¿Existe algo parecido para Ubuntu?



Gracias y un saludo

---

### Post by nopersona on 2009-08-22
Para comprimir video uso Avidemux, es muy versatil y practico, sobre todo cuando quiero pegar subtitulos a un .avi, de 800 megas deja todo entre 500 y 600, con excelente calidad de audio video, con xvid+mp3, o similares, y con una o dos pasadas. Para coprimir datos simplemente

```
sudo aptitude install rar unace unrar p7zip p7zip-full arj
```

Hay un gui llamado peazip, no lo he usado, pero lo nombran mucho. Para las imágenes solo uso Gimp e inkscape, es lo únic que necesitas. Si lo que quieres es algo más simple, revisa estos links

[http://supernetx.net/redimensionar-varias-imagenes-en-ubuntu-linux/](http://supernetx.net/redimensionar-varias-imagenes-en-ubuntu-linux/)

[http://www.alejandrox.com/2008/09/redimensionar-imagenes-masivamente-en-ubuntu-con-squash/](http://www.alejandrox.com/2008/09/redimensionar-imagenes-masivamente-en-ubuntu-con-squash/)

Aunque hay algo mejor,[ un simple script que hace todo el trabajo a dos clicks]("http://www.gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533")


Espero te sirva. Saludos

---

### Post by ivisdrek on 2009-08-26
Hola Nopersona, he instalado Avidemus, pero no lo entiendo muy bien. ¿Me podrías dar algunas indicaciones básicas de cómo funciona?

En cuanto a comprimir fotos, ¿no hay un programa específico que reduzca el tamaño sin tener que recurrir a los compresores?

¡Gracias!

---

### Post by ivisdrek on 2009-08-26
Perdona, he isntalado el Nautilus image converter, a ver qué tal me va.

Gracias y un saludo

---

### Post by AlexDDR on 2009-08-26
avidemux es muy potente y simple cuando le dedicas un pequeño tiempo, no es como el tipico programa de arrastras y convertir, pero es igual de facil, lo unico que que hay que aprender es que tu cargas el video en un editor , que le puedes aplicar filtros o cortar  etc etc. El truco es que en el panel de la izquierda eliges los formatos de salida y los configuras

Por ejemplo xvid y mp3, despues le das a guardar como y eliges el nombre y listo

Solo debes aprender un poco de conversion de videos, con lo que podras dejar tus videos con muy buena calidad (puedes ocupar 2 pasadas, mejorar los valores predeterminados del codec etc etc)

---

### Post by nopersona on 2009-08-27
Dale un ojito a lo de los scripts, es lo más fácil y funcional. Sobre Avidemux, [aquí hay un howto]("http://nopersona.wordpress.com/2008/07/18/incrustando-subtitulos-con-avidemux/#comment-33") en mi blog de cómo pegar subtitulos, en dónde sale lo de la compresión. Dos de un tiro.

---


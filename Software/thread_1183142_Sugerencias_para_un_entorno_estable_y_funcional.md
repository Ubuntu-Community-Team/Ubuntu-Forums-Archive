---
title: "Sugerencias para un entorno estable y funcional"
date: 2009-06-09
forum: Software
---

### Post by Iced_R on 2009-06-09
Eso xDD.

Necesito referencias para un entorno 100% funcional, y que me ocupe el mínimo de recuros posibles. Como puse en un post anterior, estoy intentando configurar un gestor de ventanas que se llama PekWM, y ya lo tengo con un wallpaper de fondo, una panel para las minimizaciones de ventanas, pero aún creo que me falta harto. 

Estoy usando fbpanel para el panel, y hsetroot para los wallpapers. Volví a Network Manager para las redes, pero me falta más. Por ejemplo, ¿cómo llamo al demonio que monta automáticamente los dispositivos USB? ¿Alguien sabe?

Si se me queda algo en el tintero que se pueda utilizar, porfa... acepto todas las sugerencias que haya xD.

Por si acaso, busco rendimiento xq este tarro en el que estoy trabajando tiene sólo 256 de RAM y un procesador de 2.4 GHz (un Pentium 4), y además tiene una NVIDIA GeForce MX 200 de 64 MB. Como pueden leer, reducidos recursos como para un GNOME 100% funcional.


Saludos a todos!

---

### Post by CdK1 on 2009-06-09
Se llama "hal", además nunca es malo pegar un dpkg -l y sacar lo que no necesites, así como eliminar los "servicios" innecesarios:

cd /etc/init.d/ && ls
y ve cuales no necesitas, hay herramientas como "BUM" ==> apt-get install bum luego ejecutas bum y bueno, es bastante intuitivo, tambi{en puedes recompilar tu kernel etc, hay varias cosas xDD, pero con esas caracteristícas un entorno con Gnome personalizado iría bastante bien ;)

---

### Post by Tomito on 2009-06-09
Porque no pruebas Xubuntu, este usa XFCE y es rápidisimo y muy funcional
Hace un par de años lo había probado y no me gustó, pero ahora ha avanzado mucho, de echo me cambié a este

Saludos

---

### Post by Carlos C on 2009-06-09
te sugiero mirar acá:

[http://ubuntuforums.org/showthread.php?t=1166701](http://ubuntuforums.org/showthread.php?t=1166701)

---

### Post by Iced_R on 2009-06-10
Ajajajajajaja, yo había posteado en ese topic que puso Carlos C xDDDD.

La gracia de hacerte tu propio entorno es eso, crear algo tuyo, y a tu pinta. Por eso me dio por usar PekWM. Y les pido la colaboración para saber qué cosas necesito montar para que quede un escritorio 100% utilizable, porque es lejos el entorno que menos recursos me gasta y además xq como puse con anterioridad en este post, estoy trabajando en un water de PC. Con respecto a XFCE, actualmente es casi lo mismo que instalar LXDE, y para trabajar con un clon de un entorno, mejor trabajo con el entorno original (se nota que XFCE no me gusta? xD)

Ahora, intenté con AWN para reemplazar el fbpanel, pero no cumple con la misma funcionalidad del panel que utilizaba antes. Y sigo atento a sugerencias para este entorno que quiero levantar.


Saludos.

---


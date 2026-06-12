---
title: "Problema al configurar GeForce MX4000 en KK"
date: 2009-12-04
forum: Software
---

### Post by Piero71 on 2009-12-04
hola chochamus!!

Instalé el KK en mí máquina y en la del laburo, curiosamente las dos tienen la misma placa de video (nVidia GeForce4 MX-4000) y en las dos me pasó lo mismo.

Bajé el driver de la página de nVidia y lo instalé siguiendo las instrucciones del instalador. Luego, edité el archivo xorg.conf para poder tener todas las resoluciones posibles. Hastá acá, todo bien, pero... al arbir una ventana (de lo que sea) aparece sin marco, es decir, sin la barra de título y sin los botones de minimizar/maximizar/cerrar. Puedo redimensionar la ventana, pero no moverla. Para cerrarla, tengo que ir a archivo/cerrar. Cuando abro una consola, me sale un rectángulo blanco y nada más. La consola funciona, porque si pongo "exit" a ciegas, la ventana se cierra...

¿qué puede ser? ¿hice algo mal? ¿bajé el driver equivocado? El driver que bajé es el NVIDIA-Linux-x86-96.43.14-pkg1.run

saludos y gracias!!

Ale...

---

### Post by Mauro22 on 2009-12-04
Supongo que instalaste ubuntu.

Abrí una consola y escribí:

metacity --replace

con dos guiones. Si eso anda, agrega aese comando al inicio.

---

### Post by Piero71 on 2009-12-05
> **Mauro22 said:**
> Supongo que instalaste ubuntu.

Abrí una consola y escribí:

metacity --replace

con dos guiones. Si eso anda, agrega aese comando al inicio.
Sip, como decía mas arriba, instalé el KK, es decir, el Karmic Koala... voy a probar y luego te cuento!

gracias Mauro!!

---

### Post by emiliano_raso on 2009-12-06
<comentario al margen>
Este thread no tendria que ir en Hardware?
</comentario al margen>

---

### Post by Mauro22 on 2009-12-06
> **emiliano_raso said:**
> <comentario al margen>
Este thread no tendria que ir en Hardware?
</comentario al margen>

Lo del manejador de ventanas es por Compiz y compañia... si fuera problemas de resolución seria hardware...


Creo ??? ;)

---


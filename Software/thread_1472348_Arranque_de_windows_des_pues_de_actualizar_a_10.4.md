---
title: "Arranque de windows des pues de actualizar a 10.4"
date: 2010-05-04
forum: Software
---

### Post by flakojaime on 2010-05-04
HOla nuevamente.

Bueno, acabo  de actualizar ubuntu a la version 10.4 y lo hice por medio de los paquetes en el gestor de actualizaciones.

Despues de eso, trate de usar windows para usar autocad y al elegirlo en la lista del arranque, solo se queda sin hacer nada.

Elijo windows en el grub y se queda solo el prompt parpadeando.

Trate de usar el super grub disk y no me ayudo..

Alguna pista o alguien le paso lo mismo?????

gracias!!:popcorn:

---

### Post by Carlos C on 2010-05-06
Probaste editando directamente el grub?

[http://www.guia-ubuntu.org/index.php?title=GRUB#Modificaciones_en_el_men.C3.BA_de_arranque](http://www.guia-ubuntu.org/index.php?title=GRUB#Modificaciones_en_el_men.C3.BA_de_arranque)

---

### Post by flakojaime on 2010-05-06
Gracias carloc

lo voy a intentar y te retroalimento


):P

---

### Post by pinguinosaurio on 2010-05-12
Prueba lo siguiente, en la terminal ejecuta:

sudo gedit /etc/default/grub

Busca en el archivo la siguiente  linea:


GRUB_HIDDEN_TIMEOUT=0

Y comenta la línea (osea, agrega un # a la línea) quedaría así:

#GRUB_HIDDEN_TIMEOUT=0

Guarda los cambios y cierra Gedit.

En la terminal escribe:

sudo update-grub2

Una vez que se actualice grub, reinicia la PC

Con esto ya debería aparecer el menú.

---

### Post by flakojaime on 2010-06-05
HOla

Disculpen la demora, estuve mucho tiempo tratando de solucionar el asunto.

El error se me produjo justo despues de actualizar de 9.10 a 10.4.

Al actualizar el grub, no seleccione todas las casillas de las particiones que estaban.

Despues de intentar por mucho, al final opte por lo sano y reintale todos los sistemas.

Bueno, igual perdi ciertas configuraciones de ubuntu que me costo dejarlas como reloj (como el control de ventiladores y temperaturas), pero es el costo.jejejeje


saludos y gracias por todos sus comentarios:guitar:

---

### Post by RafaelG on 2010-06-11
> **flakojaime said:**
> Despues de intentar por mucho, al final opte por lo sano y reintale todos los sistemas.

                   [SIZE=4]Por ese motivo prefiero realizar una instalacion en limpio, aunque yo no tengo windows desde el arranque solo lo tengo en VirtualBox. Una de las novedades en el 10.4 LTS fue el nuevo Grub el cual es mas practico para realizar modificaciones como por ejemplo: tiempo de espera, imagen de partida y pocisiones de los sistemas en el arranque. Todo esto en cierto modo para mi  es mas practico con el nuevo Grub en comparacion al antiguo.[/SIZE]

---


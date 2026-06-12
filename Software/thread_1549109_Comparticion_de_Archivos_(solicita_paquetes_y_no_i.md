---
title: "Comparticion de Archivos (solicita paquetes y no indica cuales)"
date: 2010-08-09
forum: Software
---

### Post by atari130xe on 2010-08-09
Nuevamente en el foro, intento compartir carpetas (ambas dentro de Ubuntu 10.04) mediante LAN y Switch que a su vez comparten internet mediante este último sin inconveniente alguno y de manera independiente, pero al ir a "Sistema ---> Preferencias ---> Compartición de archivos personales me sale el siguiente aviso:
[IMG]http://a.imageshack.us/img835/3039/comparticion.png[/IMG]
el tema es que no me dice QUE paquetes necesito instalar para poder compartir archivos entre las 2 PC alguien podría orientarme al respecto, es la primera vez que intento hacer esto, y lo que encontré en la red habla de que este aviso "solicita" la contraseña de usuario para instalar los paquetes faltantes pero en mi caso eso no ocurre, solo me avisa que no están instalados pero no cuáles son necesarios.
gracias!

---

### Post by atari130xe on 2010-08-09
Solucionado. Activé el repositorio Ubuntu Lucid partner, luego instale samba con sus dependencias, cerré y abrí sesión para finalmente:

```
sudo nautilus
``` seleccioné la carpeta luego "compartición de archivos" en el menú contextual y listo ya puedo ver los archivos desde mi pc. :p

PD: Por algún motivo que desconozco, ir a "Sistema ---> Preferencias ---> Compartición de archivos en mi PC no funciona.

---


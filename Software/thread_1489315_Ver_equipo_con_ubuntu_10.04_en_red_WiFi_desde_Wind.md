---
title: "Ver equipo con ubuntu 10.04 en red WiFi desde Windows 7"
date: 2010-05-21
forum: Software
---

### Post by Matnet on 2010-05-21
Hola de nuevo,

ahora estoy experimentando con redes, y intento hacer trabajar en conjunto a un desktop con Windows 7 Ultimate y un notebook con Lucid vía WiFi. (por cierto, encontré la solución en [http://ubuntuforums.org/archive/index.php/t-482636.html](http://ubuntuforums.org/archive/index.php/t-482636.html) )

Ubuntu entra perfectamente a las carpetas compartidas de Windows, pero no al revés. No estoy seguro de si es Lucid el que no se deja ver o seven el que no ve (sospecho esto último, es windows... :P)

Tal vez si es el último caso este post esté descontextualizado, pero puede que alguno de ustedes lo haya hecho y me funcione.

Debe influir además que el Módem WiFi sea un ZTE ZXV10 W300 con firmware de Movistar

Muchas gracias desde ya

MatNet

---

### Post by bichopro on 2010-05-22
toma cualquier carpeta, dale boton derecho compartir, te pedirá instalar ciertos paquetes para poder compartirla, instala, si no deseas compartir la carpeta quitale la opción, después de instalar los paquetes anteriores tu ubuntu ya esta listo para verse en una red windows

---

### Post by Matnet on 2010-05-22
> **bichopro said:**
> toma cualquier carpeta, dale boton derecho compartir, te pedirá instalar ciertos paquetes para poder compartirla, instala, si no deseas compartir la carpeta quitale la opción, después de instalar los paquetes anteriores tu ubuntu ya esta listo para verse en una red windows

muchas gracias, pero no me funcionó...

---

### Post by asterix77 on 2010-05-24
¿es una red de tipo ad-hoc?

Para saber si la conexión desde windows está activa, abre la terminal en windows y hace un ping a la ip de lucid, si hay respuesta lo más probable es que lucid le esté negando el servicio a windows.

También puedes intentar abrir el explorador de carpetas de windows, y escribir la dirección ip de lucid en la barra, y ver que sucede. A veces este método funciona.

otra pregunta ¿ambas máquinas pertenecen al mismo grupo de trabajo?

Saludos

---


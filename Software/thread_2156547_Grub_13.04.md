---
title: "Grub 13.04"
date: 2013-06-22
forum: Software
---

### Post by layevska on 2013-06-22
Hola, hay un problema que no habia tenido nunca, la instalacion es correcta pero al reiniciar el ordenador no aparece la opcion ubuntu, me aparece que esta instalado, incluso via live CD pude ver los archivos y el directorio de super usuario. Pero no hay manera de seleccionar para iniciar con el nuevo sistema instalado, no tengo ningun otro sistema instalado

Desde ya, gracias!

---

### Post by guillermolisi on 2013-06-22
Normalmente el menu de Grub mostrando otras opciones de inicio aparece cuando hay mas de un sistema operativo instalado o cuando se lo configura para que sea visto al inicio, aun con un solo sistema operativo instalado.

Existe la posibilidad de forzar su visualizacion presionando una tecla al inicio, normalmente Esc, apenas se deja de ver la pantalla de inicio del BIOS de la maquina.

No me reaulta del todo claro si es esto lo que consultas o es que no se inicia el sistema.

---

### Post by layevska on 2013-06-22
Lo instale pero no inicia y no aparece ningun grub para iniciar, solo el que me habia dejado windows

---

### Post by gmunioz on 2013-06-24
En una sesión live.
Abre un terminal y ejecuta en ella:
> sudo su
fdisk -l
copia y pega la salida en el post.

---


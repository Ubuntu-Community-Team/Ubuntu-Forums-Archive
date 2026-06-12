---
title: "No encuentro menu.lst en Grub"
date: 2010-07-27
forum: Software
---

### Post by nicfer on 2010-07-27
Hola gente.

Yo estoy usando hace rato esta distro, por ahora no tuve grandes problemas, solo dos que no son muy urgentes.

Al iniciar la compu el GRUB me muestra como 10 opciones distintas de arranque (por todas las veces que actualizé el 'kernel'). El problema reside en que no encuentro el archivo que se encarga de mantener esa lista (menu.lst), que tendría que estar en /boot/grub y no se bien si está en otro lugar o bajo otro nombre.  ¿Alguno me daría un dedo en esto?

Saludos cordiales.

---

### Post by biale on 2010-07-28
Hay dos puntos para considerar. El primero es que grub cambio de versión y el menu.lst desapareció. El manejo es bien distinto. Trata de ubicar en la web algún tutorial que mensione a "Grub 2" (Grub 1.98 para Lucid). Hay también material en el foro.

El segundo es salir del problema eliminando los kernels antiguos. Los ubicas en /boot como vmlinuz-2.6...

Anota bien en un papel los números y asegurarte de respetar (no borrar!) los dos ultimos. En mi caso tendría que respetar por lo menos a vmlinuz-**2.6.32-24**-generic y a vmlinuz-**2.6.32-23**-generic.

Usando synaptic podes desintalar los kernels mas viejos. Los ubicas haciendo una busqueda con los códigos numericos para luego desinstalarlos.

El comando "sudo update-grub" se encarga modificar el archivo /boot/grub/grub.cfg y generar el nuevo menu de grub.

---

### Post by nicfer on 2010-07-28
Ya veo. Lo que quería era mover y quizás 'ocultar' algunas entradas (de forma que sólo quedara una por cada SO, de forma que no sean visibles las de arranque de emergencia o los 'memtest' a menos que pulse determinada tecla (como el truco de mantener presionado 'shift' al inicio)) para no tener que presionar 5 veces abajo para iniciar windows (o para iniciar ubuntu si configuro ventanas como por defecto). Parece que para eso hay que configurar un tal archivo /etc/grub.d/40_custom pero ahora me fijo mejor como es el asunto.

Saludos.

---

### Post by biale on 2010-07-29
La funcionalidades estan muy distribuidas en varios archivos de configuracion. Vas a tener que leer en forma bastante completa y verificar lo que quedó en grub.cfg antes de reiniciar. 

40_custom es para agregar cosas, no para quitar por si mismo.

---


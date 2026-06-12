---
title: "Ayuda ubuntu no inicia"
date: 2009-12-21
forum: Software
---

### Post by santiago79 on 2009-12-21
HOLA GENTE TENGO UN PROBLEMA QUE NOSE POR DONDE APUNTAR PARA SOLUCIONARLO, LA COSA ES ASI:
YO TENGO UN DISCO DE 80 gb UNA PARTICIÓN DE 20 CON UBUNTU, OTRA DE 20 EN FAT32 PARA LA MUSICA Y UNA DE 40 CON KUBUNTU
LA COSA ES QUE NOSE QUE PASO QUE HOY PRENDO LA PC Y QUIERO INICIAR UBUNTU Y NO PUEDO ME SALE ESTO

[IMG]http://g.imagehost.org/view/0746/DSC06936[/IMG]

ES UNA MACANA PORQUE YO KUBUNTU NO LO USO PORQUE MUCHO NO ME GUSTA EL KDE Y EN EL DISCO DE UBUNTU TENGO TODAS MIS COSAS
SI INICIO DESDE LIVE CD LA PARTICIÓN CON UBUNTU LA VE, PERO SI INICIO CON KUBUNTU NO SOLO VE LA FAT32
ALGUIEN QUE ME AYUDE 
ME TOMO DE IMPREVISTO ESTO :(

por si no ven la imagen les dejo el link aca:
[http://g.imagehost.org/view/0746/DSC06936](http://g.imagehost.org/view/0746/DSC06936)

---

### Post by euzkoarima on 2009-12-21
según [esta pág]("http://entidadweb.blogspot.com/2009/02/ubuntu-810-alert-devdiskby-uuid-no.html")

> Alert /dev/disk/by-uuid/xxxx does not exist dropping to a shell

Tras varias búsquedas en google parece que el problema es debido no al Grub si no al Kernel y lo que tiene que esperar Ubuntu para reconocer la partición.

El problema se soluciona añadiendo un retardo en el comando de Grub.

Cuando arranquemos la máquina esperamos al menu de Grub y pulsamos ESC. Seleccionamos la primera entrada de la lista y pulsamos e para editarla.

Después seleccionamos la línea de kernel y añadimos el comando rootdelay=130 tal y como sigue:

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash rootdelay=130

Por último, salir de la línea con return y luego pulsar b para arrancar ubuntu. 

Según el thread en inglés que citan como fuente, le funcionó a varios en distintas versiones de ubuntu.

Saludos,
Eduardo

---

### Post by santiago79 on 2009-12-21
no sigue igual ya probé muchas posibles soluciones que encontré buscando y nada :confused:

---


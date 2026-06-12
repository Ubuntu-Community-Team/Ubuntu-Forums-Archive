---
title: "Archivos de Configuración de LAyout"
date: 2009-09-22
forum: Software
---

### Post by alehawk on 2009-09-22
Hola, hice un xfs_repair y no levanto mas mi ubunto por lo que voy a aprovechar para formatear y sacar toda la basura del sistema.
Queria saber si me podrian indicar donde se encuentran lso archivos que guardan la informacion de la parte estetica del gnome, o sea, colores, fondo de escritorio, etc, la idea es copiarlos antes para, una vez instalado el nuevo, restaurarlos asi me queda el escritorio como estaba antes.
Muchas gracias!!

---

### Post by gmunioz on 2009-09-22
Hola ale....:

En /home/usuario/.gnome2

Te sugiero:

1) Instales en cuatro particiones:
/ primaria unos 14 gigas
swap logica 2 gigas
/home logica 5 ò 6 gigas
/home/usuario/datos lógica del resto de los gigas

2) Uses sistema de archivos ext4, es superior a 
reiserfs y xfs

3) Pongas a salvo todo tu /home/usuario para guardar 
todas las configuraciones, no solo gnome.

---

### Post by staar on 2009-09-22
también sería recomendable que guardes los temas que tengas, para que no tengas que bajarlos de nuevo, estos se guardan en */home/tuusuario/.themes* para los gtk y en */home/tuusuario/.icons* para los iconos...

saludos

---


---
title: "problemas con grub y xp"
date: 2009-03-05
forum: Software
---

### Post by infernus92 on 2009-03-05
hola... hace un rato apague mi computadora desde xp... saque los 2 discos que tengo (uno con xp y el otro con Intrepid) y puse un disco para probarlo... nunca arranco. pero ese no es el problema...
cuando volvi a poner mis discos (todo esta bien conectado... lo revise varias veces) intente iniciar xp... pero cuando selecciono iniciar xp desde el grub, me aparece Error 13... dice algo como que el formato no es compatible o algo asi...
pero yo monto ese disco desde ubuntu y lo puedo usar lo mas bien... y obviamente, no se cambio el formato para nada...
si alguien me puede dar alguna idea por favor... tambien me quise bajar el supergrub para intentar desde ahi... pero la imagen ISO pesa 4.4 MB... puede ser?? por si las dudas no lo grabe porque tengo un solo cd virgen

---

### Post by staar on 2009-03-05
en la bios, el orden de inicio sigue siendo el mismo que antes? fijate eso, tambien fijate si el orden de los discos es el mismo que antes, es casi seguro que el grub esta buscando windows en otra particion, y si, el supergrub disk es livianito...

para que podamos ayudarte mejor postea la salida de este comando ```
fdisk -l
``` y el contenido de este archivo ```
/boot/grub/menu.lst
```

saludos

---

### Post by infernus92 on 2009-03-06
gracias staar...pero me fije en la prioridad de los discos antes de leer tu post y ese era el problema... se habia cambiado y seguramente el grub estaba buscando windows en cualquier lado... gracias igual :)

---


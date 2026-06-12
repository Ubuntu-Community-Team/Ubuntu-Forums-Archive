---
title: "Arranque de S.O (winxp - Karmic)"
date: 2009-11-01
forum: Software
---

### Post by checudero on 2009-11-01
Hola a todos!!!
Una consulta, quiero instalar el Karmic pero tengo windows y es sabido que el windows no me va a dejar botear el karmic cuando arranque la netbook.
¿Que hago en este caso, para que me aparesca la pantalla para elegir los S.O?
Gracias

---

### Post by santiagoward2000 on 2009-11-01
> **checudero said:**
> Hola a todos!!!
Una consulta, quiero instalar el Karmic pero tengo windows y es sabido que el windows no me va a dejar botear el karmic cuando arranque la netbook.
¿Que hago en este caso, para que me aparesca la pantalla para elegir los S.O?
Gracias

Bienvenido!
Cuando instalás Ubuntu, el instalador detecta si hay otro S.O. y configura solo grub (el arranque que usa Ubuntu) para que puedas elegir a qué S.O. entrar (grub sobreescribe el MRB y saca el de Windows).
En realidad si querés que lo haga Windows podés, pero es un poco más complicado. Si no tenés ninguna otra partición rara dando vueltas, te recomiendo que uses el de Ubuntu.
Saludos, y suerte!

---

### Post by nemodot on 2009-11-01
Hace una partición desde windows para ubuntu y hace una pequeñita para el espacio de memoria de intercambio swap. Luego booteas con el cd del Karmic y en el menú de instalación elegis el comando manual de las particiones, seleccionas la partición que hiciste para ubuntu previamente y le situas la barra " / " para especificar que ahi queres que se instale, ademas activa la casilla para formatear la partición y siguiente le das.

---

### Post by josecuervo86 on 2009-11-01
O podes seguir este tutorial: [http://ubuntuforums.org/showthread.php?t=1280260](http://ubuntuforums.org/showthread.php?t=1280260)

Esta hecho para Jaunty (9.04) pero se aplica tambien para Karmic (9.10)

---


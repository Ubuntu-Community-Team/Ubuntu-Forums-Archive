---
title: "[SOLVED] Personalizar -- Sistema -&amp;gt; Salir..."
date: 2008-07-06
forum: Software
---

### Post by electronpositivo on 2008-07-06
Buenas,

Me gustaría saber si se pueden personalizar las opciones que aparecen para apagar el equipo al pulsar en Sistema -> Salir.

Por ejemplo, ¿se pueden deshabilitar o hacer desaparecer las opciones de suspender y hibernar?

Supongo que existirá algún fichero para configurarlo, pero no tengo idea.

Gracias por la ayuda

---

### Post by sdennie on 2008-07-06
Fijate en gconf-editor: /apps/gnome-power-manager/general.  Sin "can_suspend" y "can_hibernate", no vas a ver esas opciones.

---

### Post by electronpositivo on 2008-07-07
Era eso lo que buscaba!

Muchas gracias :guitar:

---

### Post by niko_3100 on 2008-07-07
Funciono??

---

### Post by electronpositivo on 2008-07-07
Perfectamente. =D>

---


---
title: "Cambiar los iconos en el area de notificacion."
date: 2009-10-05
forum: Software
---

### Post by emiliano_raso on 2009-10-05
Alguien sabe como se editan los iconos de las aplicaciones en el area de notificación?

Porque por ejemplo mas de una vez he puesto un theme de iconos en blanco y negro, pero los iconos de aplicaciones como Pidgin, emesene, Opera, etc, son en colores y nunca cambian.

Hay forma de cambiarlos o personalizarlos?

---

### Post by ermeyers on 2009-10-05
English Translation: [http://babelfish.yahoo.com/](http://babelfish.yahoo.com/)
To change the icons in the notification area. Somebody knows as the icons of the applications in the notification area are published? Because for example but in one go I have put theme of icons in black and white, but the icons of applications like Pidgin, emesene, Operate, etc, are in colors and they never change. There is form to change them or to personalize them?

---

### Post by ermeyers on 2009-10-05
dpkg -L pidgin
view /usr/share/applications/pidgin.desktop
```

Icon=pidgin

```
find /usr/share/icons/ -name '*pidgin*'

---

### Post by santiagoward2000 on 2009-10-05
> **emiliano_raso said:**
> Alguien sabe como se editan los iconos de las aplicaciones en el area de notificación?

Porque por ejemplo mas de una vez he puesto un theme de iconos en blanco y negro, pero los iconos de aplicaciones como Pidgin, emesene, Opera, etc, son en colores y nunca cambian.

Hay forma de cambiarlos o personalizarlos?

Hola!
Yo la única forma que encontré de cambiar los tray-icons del Pidgin fue reemplazando manualmente los que se encuentran en la carpeta **/usr/share/pixmaps/pidgin/tray**. No sé si hay alguna forma más prolija.
Yo al final me cansé, porque tenía que volver a cambiarlos después de cada actualización, y dejé los que vienen por defecto.
Saludos!

---

### Post by rubioo on 2009-10-05
Hola emiliano, yo tenia un [problema parecido]("http://ubuntuforums.org/showthread.php?t=1197800"), pero solo logre cambiar el icono de GUFW.

---

### Post by emiliano_raso on 2010-06-15
> **santiagoward2000 said:**
> Hola!
Yo la única forma que encontré de cambiar los tray-icons del Pidgin fue reemplazando manualmente los que se encuentran en la carpeta **/usr/share/pixmaps/pidgin/tray**. No sé si hay alguna forma más prolija.
Yo al final me cansé, porque tenía que volver a cambiarlos después de cada actualización, y dejé los que vienen por defecto.
Saludos!

Esta es la solucion. Gracias.

---


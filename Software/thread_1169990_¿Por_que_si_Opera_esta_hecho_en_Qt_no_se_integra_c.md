---
title: "¿Por que si Opera esta hecho en Qt no se integra con KDE?"
date: 2009-05-25
forum: Software
---

### Post by pol666 on 2009-05-25
Simplemente eso, dicen que Opera esta hecha con QT sin embargo no se adapta al tema en uso de KDE4  como si pasa en Firefox y GTK. ¿COmo es eso?

---

### Post by andy_91 on 2009-05-25
no esta hecho en qt3??? :confused: no pasa lo mismo con el virtualbox??? :confused:

---

### Post by pablo.s on 2009-05-25
[A ver]("http://my.opera.com/kilsmo/blog/2008/01/29/opera-is-not-based-on-qt")...

---

### Post by andy_91 on 2009-05-25
a ok eso resuelve un poco mis dudas

> Opera is not based on Qt

Opera has never been based on Qt. Opera developed its own lightweight portability layer, to be able to move to all kinds of platforms, even where no cross platform toolkits are available. Opera for Linux is using Qt the same way as Opera for Windows is using Windows API:s to connect to the platform.

---

### Post by staar on 2009-05-25
bueno, no esta basado, pero en todo caso la versión de linux usa QT, el problema es que usa sus propias librerías (que te vienen en el deb) no las del sistema, por eso no se integra...

en realidad se lo puede hacer usar el tema del sistema (a través de QtConfig, o lanzándolo con una opción específica) pero solo en la barra de menús, en los menus y en algunos botones, el resto depende del programa...

también depende de la versión, la estable actual 9.64, creo recordar que está en Qt3, en cambio las previews y la alpha de la versión 10, tienen una versión en Qt4, e inclusive hay forma de obligarlo a usar las librerías del sistema, para que se adapte al theme...

saludos

---

### Post by pol666 on 2009-05-25
> **andy_91 said:**
> no esta hecho en qt3??? :confused: no pasa lo mismo con el virtualbox??? :confused:

Virtual Box es Qt4.
---------------------

Ah bien, gracias staar.

---


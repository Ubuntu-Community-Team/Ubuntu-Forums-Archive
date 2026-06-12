---
title: "Apariencia aplicaciones kde en Gnome"
date: 2010-01-24
forum: Software
---

### Post by NickCis on 2010-01-24
Hola, uso un par de aplicaciones de Kde bajo mi ubuntu 9.10, y algo que me molesta mucho es que tenga un tema de colores tan distinto al de Gnome.

Hay alguna manera que las aplicaciones de kde, adopten el tema de Gnome y asi mas o menos respetar los colores e iconos?.

Saludos.

---

### Post by juancarlospaco on 2010-01-24
Ponerle un tema de KDE similar, 
pero tendrias que instalar mas que el kdelibs base para poder cambiar el theme,
no recuerdo el nombre del programa que controla los themes.

---

### Post by mama21mama on 2010-01-24
[QGtkStyle]("http://mamalibre.eshost.com.ar/?q=node/122") es un "estilo" de Qt rendeado usando la máquina de temas de GTK+ para dar a las aplicaciones típicas de KDE una apariencia nativa cuando ejecuten en un escritorio GNOME

con esto se supone que debe de usar los controles gtk

---

### Post by NickCis on 2010-01-25
Ahi lo instalo y veo qe onda,,,
Estube buscando por google acerca del qgtkstyle (por que me parecio raro que no este en los repositorios de 9.10), puede ser que sea algo viejo o qe ya este incluido en algun paquete de kde? (lei algo de que viene con Kde 4.5 o algo asi)...

By the way, me traera algun problema qe el ppa sea para ubuntu 9.04? (uso 9.10).

Saludos.

Edit: no lo pude instalar desde el Ppa, por lo que lei, ya viene incluido en ubuntu 9.10 en las qtlibs... Instale qt4-qtconfig y ahora ando peleando con ello, cualquier ayuda viene bien =P

Edit 2: Aunque el qt4-qtconfig me diga que estoy usando el tema Gtk (y este se ve bien de acuerdo al tema Gtk) otras aplicaciones de Kde, como Kmess (2.0.2) se siguen viendo como se veian ants (bien kde). Si miro el about Kde de las aplicaciones me dice que estan usando KDE 4.3.2, en cambio la del qt4-qtconfig dice que esta usando QT 4.5.2, tiene algo que ver esto?, como puedo solucionar mi problema?

---

### Post by juancarlospaco on 2010-01-25
Fijate un paquete llamado QTCurve...

---

### Post by NickCis on 2010-01-25
Instale ese paquete, pero no entiendo qe debe hacer =S,,, xD jajaj

Alguna ayudita para un poco entiendod en el tema? jaja...

Lo que no enitnedo es por qe si el Qt4Config, esta configurado como yo quiero que sea (usa el tema Gtk), las aplicaciones de Kde, no lo hacen =S...

Saludos.

---

### Post by juancarlospaco on 2010-01-25
*mmm... *mira que para que sirva, tienen que depender exclusivamente de KDELibs,
o sea hay programas que dependen de QT y no de KDELibs.
:)

---

### Post by NickCis on 2010-01-25
Mmm,,, Creo qe algo estoy entendiendo,,, pero sigo sin poder configurar el aspecto (va lograr algo parecido),,, Instale el qt4-qtconfig, de ahi configure para que copie el aspecto Gtk (y eso lo copia bien, va, el qt4-qtconfig tiene bien el aspecto).

El problema seria qe aplicaciones como k9copy o kmess (2.0.2), estarian dependiendo de librerias de Kde, entonces su estetica no depende del qt4-qtconfig, no?. (La flashee mal o es asi?).

Ahi entra el Qtcurves, no? osea, me tendria que "unificar" el aspecto o algo asi?.
Lo instale, pero que tengo que hacer?. (instale el paquete desde aptitude)

Saludos y muchas gracias por responder =P.

---


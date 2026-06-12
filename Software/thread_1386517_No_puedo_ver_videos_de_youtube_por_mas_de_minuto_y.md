---
title: "No puedo ver videos de youtube por mas de minuto y medio"
date: 2010-01-20
forum: Software
---

### Post by Seba_83 on 2010-01-20
Hola a todos, instale recientemente ubuntu 9.10, con escritorio gnome.  El problema es que cuando comienzo a ver un video on line, de cualquier sitio, al minuto y medio aprox se queda congelado el sistema, no funciona nada.  el otro problema es que soy bastante nuevo en linux y no se que otros datos necesitan para ayudarme.
tengo instalado jre, la ultima version, y navego con chrome y mozilla.  Gracias de antemano.

Seba.

---

### Post by vargux on 2010-01-21
mmm... quizás algo que sea de utilidad sería que mencionarás tu PC/Notebook que posees.... algunas especificaciones si es que posees una tarjeta de video especial... esas cosas, ya que quizás te falte algún controlador por ahí....

Por otro lado, estos problemas tienen relación a Firefox/Chrome + Flash.... 
quizás no tienes instalado correctamente el flash... revisa con ```
sudo apt-cache policy flashplugin-nonfree 
```... si no lo tienes instalado, entonces lo haces con ```
sudo apt-get install flashplugin-nonfree 
``` (todos los códigos desde una términal ....está en Menu Ubuntu > Accesorios > Terminal)....

Pero es importante conocer los datos de tu máquina.

---

### Post by Seba_83 on 2010-01-21
Muchas Gracias, la verdad que los comando funcionaron a la perfeccion y ya se ve bastante bien los videos online.
solo para que quede en antecendente, tengo un HP 530, core duo de 1.6, 1.5GB Ram, video integrado del mas penquita.

gracias de nuevo!

---

### Post by xtremox on 2010-02-09
hola yo tenia el mismo problema y lo solucione poniendo

> sudo aptitude install ubuntu-restricted-extras

ese comando me instalo el soporte para mp3,flash y unas fuentes que hacen que se vean mejor las webs
ojala te sirva

---


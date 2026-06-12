---
title: "Volver a Gimp 2.6 !"
date: 2010-01-07
forum: Software
---

### Post by FB91 on 2010-01-07
Quise instalar el Gimp 2.7, para ello hice lo siguiente:

```
sudo sh -c "echo 'deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main' >> /etc/apt/sources.list"

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 405A15CB

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install libgegl-0.0-0
```

pero ahora lo quiero desinstalar y volver al viejo gimp 2.6 (ya que el 2.7 me daba algunos errores)

Entonces lo que hice fué borrar el nuevo repositorio que agregué, eliminar la llave (key), elimine gimp, hice un "update" e instalé de nuevo gimp (2.6)

Pero cuando se terminó de instalar y lo quiero iniciar me sale este error (en consola)
```
gimp-2.6: error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory
```

probé algunas soluciones que encontré en unos foros en inglés pero sigo sin poder resolverlo...

alguna idea? gracias :D

---

### Post by juancarlospaco on 2010-01-07
sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean

:)

---

### Post by FB91 on 2010-01-07
> **juancarlospaco said:**
> sudo apt-get update ; sudo apt-get purge gimp libgegl* libbabl* ; sudo apt-get install gimp ; sudo apt-get clean

:)

Muchas gracias! me funcionó 10 puntos :D

---

### Post by juancarlospaco on 2010-01-08
Es que yo tambien tube que volver, los .GIF me guardaba 1 solo Frame
:)

---

### Post by waloleles on 2010-01-16
MUchisimas gracias, ya me estaba volviedo loco!!!!!!.

---

### Post by maghoxfr on 2010-10-25
Me salvaste la vida!

---


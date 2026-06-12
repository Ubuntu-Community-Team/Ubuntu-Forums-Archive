---
title: "[SOLUCIONADO] Skype en Ubuntu 9.04"
date: 2009-07-14
forum: Software
---

### Post by Naldylipu on 2009-07-14
Hola! estaba tratando de instalar skype en ubuntu 9.04
seguí la guía que aparece en [http://ubuntuway.wordpress.com/2009/05/12/skype-en-ubuntu-9-04/](http://ubuntuway.wordpress.com/2009/05/12/skype-en-ubuntu-9-04/) el problema es que al bajar el paquete skype (el 2do) me aparece lo siguiente 
```
 Error: La dependencia no se puede satisfacer: libqt4-dbus (>= 4.4.3)
```
¿que hago para poder usarlo?

---

### Post by nopersona on 2009-07-14
Esa librería está en jaunty-updates, asegúrate de tener activada la casillas en los repositorios. Luego la buscas en synaptic, o más fácil aún:

```
sudo apt-get install libqt4-dbus
```


 O si no, activa el [repositorio medibuntu]("http://livinlavidalinux.wordpress.com/2009/06/18/como-agregar-repositorio-medibuntu-a-ubuntu-jaunty/").

---

### Post by Naldylipu on 2009-07-15
> **nopersona said:**
> Esa librería está en jaunty-updates, asegúrate de tener activada la casillas en los repositorios. Luego la buscas en synaptic, o más fácil aún:

```
sudo apt-get install libqt4-dbus
```
 O si no, activa el [repositorio medibuntu]("http://livinlavidalinux.wordpress.com/2009/06/18/como-agregar-repositorio-medibuntu-a-ubuntu-jaunty/").

tenia que ver con los origenes del software, no tenia marcadas las casillas correctas, el problema ya está solucionado :D

gracias!!

---


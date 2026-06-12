---
title: "Ha ocurrido un error al crear el proceso hijo para esta terminal"
date: 2009-05-01
forum: Software
---

### Post by Hielasangre on 2009-05-01
Buenas tardes a todos. Soy nuevo por aquí.
Si el chequeo funciona, éste tema no ha sido tocado. Además con el buscador no encontré nada.
Llevo mucho tiempo usando Ubuntu, las nuevas versiones siempre las arranco de beta y nunca tengo que realizar un nuevo fresh install.
Sin embargo, algo raro ocurrió durante la última actualización de mi Jaunty Jackalope. Ya no puedo utilizar gnome-terminal.
El error que obtengo es el siguiente:
**Ha ocurrido un error al crear el proceso hijo para esta terminal**
En una ventana emergente y luego de cerrarla, sólo queda abierto lo que sería el frontend, o sea una terminal vacía, que no dá prompt, no tiene bash, no acepta nada que escriba, etc.
Probé con la solución que proponían varios. Agregar una línea como la siguiente al fstab y remontar todo:
**devpts          /dev/pts        devpts          gid=5,mode=620  0       0**
Pero nada cambió, sigo con el mismo problema.
Si alguno tiene idea de qué debo revisar, se los agradecería.
Saludos.
):P

---

### Post by staar on 2009-05-01
según este bug: [https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927]("https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927"), otra solución es esta (traducción rápida by me, chiflá si no entendés :-P :-D) :

1. El orden en /etc/rcS.d esta mezclado. Fix:

```
$ ls /etc/rcS.d | grep mountdevsubfs.sh
```
            Anotá el número al lado de la "S" en la salida (ej. el 05 en S05mountdevsubfs.sh).

```
$ sudo mv /etc/rcS.d/S_mountdevsubfs.sh /etc/rcS.d/S11mountdevsubfs.sh
```
            donde _ es el número que anotaste.

2. O, si modificaste /etc/init.d/mountdevsubfs.sh (para hacer andar VirtualBox; un workaround que ya no es necesario) y dpkg se niega a actualizarlo (bug 360160). Fix:

```
$ sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh
```

saludos

---

### Post by Hielasangre on 2009-05-02
Gracias Staar.
Pero a **mountdevsubfs** lo tengo en S11 ya, y el error persiste.
Terminator tampoco funciona y la reinstalación forzada de gnome-terminal no me ha solucionado nada.
Un dato curioso: **Guake-Terminal** funciona bien.:-k
Pero extraño mi terminal :(
Saludos.

---


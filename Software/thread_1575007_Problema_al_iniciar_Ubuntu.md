---
title: "Problema al iniciar Ubuntu"
date: 2010-09-15
forum: Software
---

### Post by dam1977 on 2010-09-15
Uso en mi trabajo una vieja Pentium IV con 2 gigas de RAM, placa de video y un disquito de 80 gigas. En estos días acabo de eliminar por completo la partición de XP. Tengo solo Ubuntu 10.04 y una máquina virtual con XP. Anda todo una maravilla. Pero hice lio en un momento y reinicié. al reiniciar me apareció esto:

Ocurrió un error cuando se montaba /proc/bus/usb
Pulse S para omitir el montaje o M para recuperar manualmente

A partir de entonces siempre ocurre lo mismo. Yo pulso S y trabajo casi bien (digo casi porque despues de un rato de trabajar con el XP en la máquina virtual el teclado no responde. No se si tendrá relación).
Estuve mirando la carpeta /proc/bus/usb y lo último, usb, no existe. Me imagino que busca una carpeta que desapareció o algo así.

---

### Post by guillermolisi on 2010-09-15
Como es el contenido del archivo /etc/fstab ?

---

### Post by dam1977 on 2010-09-15
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0

Gracias!!!

---

### Post by guillermolisi on 2010-09-15
Comentale la ultima linea con un # en la primera posicion (margen izquierdo).

Tiene que verse asi
```
#none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```

Esa entrada en fstab se utilizaba para darle funcionalidad a los dispositivos USB de VBox en Karmic (o version contemporanea a ella).

Parte de la info la tome de [aqui]("http://www.ubuntu-es.org/node/132846")

---

### Post by dam1977 on 2010-09-15
Solucionado. Puse el signo # al final de esa linea del fstab y chau problema.
Como siempre, agradecido

---

### Post by javierch on 2010-09-24
Tengo ese mismo problema pero no puedo editar el archivo fstab. Que puedo hacer?

---

### Post by guillermolisi on 2010-09-24
> **javierch said:**
> Tengo ese mismo problema pero no puedo editar el archivo fstab. Que puedo hacer?
Cuando lo edites tenes que anteponer "sudo" (sin las comillas) y luego el resto de los comandos
```
sudo <nombre_del_editor> /etc/fstab
```
Te pedira una clave que no es otra que la del usuario que estas utilizando y que, generalmente, es el que se creo en tiempo de instalacion del sistema.

---

### Post by juancarlospaco on 2010-09-24
sudo xdg-open /etc/fstab

Abre con el editor de texto por defecto.
:)

---


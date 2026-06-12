---
title: "Hacer copia de Seguridad DVD Xbox360 (pregunta)"
date: 2009-07-07
forum: Software
---

### Post by jpoeta on 2009-07-07
Hola amigos de Loco team Argentina, 
Quisiera saber si es posible y como se puede hacer una copia de seguridad de un juego de xbox 360 con ubuntu Linux
Me refiero a copiar un iso de un original y luego quemar el iso
Jpoeta:guitar:

---

### Post by gmunioz on 2009-07-09
Hola jpo...:

Verificar si estan instaladas y si no lo estan, instalar:

dvdbackup

dvd+rw-tools

Mediante synaptic o mediante apt-get

sudo apt-get install dvdbackup dvd+rw-tools

Para extraer la estructura completa de un dvd al disco rígido se usa

dvdbackup

Si suponemos que /dev/dvd es el archivo que usa el sistema para acceder

al lector/grabador de DVD 

sudo dvdbackup -M -i /dev/dvd -o /home/usuario/dvdbackups

Para restaurar esa estructura a un DVD virgen se usa growisofs 

sudo growisofs -Z /dev/dvd -dvd-compat /home/usuario/dvdbackups

para mas información 

man dvdbackup

man growisofs

O lo mas sencillo usar el comando dd

Poner el dvd original, desmontarlo y ejecutar

sudo dd if=/dev/dvd of=/tmp/mi_imagen.iso

sacar el dvd original, poner el grabable y ejecutar

sudo dd if=/tmp/mi_imagen.iso of=/dev/dvd

---


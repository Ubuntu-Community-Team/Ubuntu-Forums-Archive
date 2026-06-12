---
title: "Error Initramfs (solucionado)"
date: 2010-07-15
forum: Software
---

### Post by Eduardo Natali on 2010-07-15
Error Initramfs solucionado

Hola, resultó que, después de reiniciar el PC me salió la pantalla negra con el fatídico error:

BusyBox v1.1.3 (Debian 1:.1.3-3-ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can´t access tty; job control turned off

(initramfs)

Estuve buscando pero hay muy pocas soluciones para ese error, aprovecho para compartir como lo solucione:

-> insertar el Live CD -> escoger la opción "Probar ubuntu sin alterar su equipo"
> una vez ya en la pantalla de Gnome -> Preferencias -> Añadir software y descargamos Gparted
-> Abrimos Sistema -> Gparted -> Check, eso examina y repara el error, una vez finalizado el chequeo reiniciar, retirando el Live CD y el sistema vuelve a funcionar con total normalidad, así de fácil.

Saludos y Que tengáis suerte!
Eduardo Natali
fuente:[http://www.ubuntu-es.org/node/126191](http://www.ubuntu-es.org/node/126191)

---


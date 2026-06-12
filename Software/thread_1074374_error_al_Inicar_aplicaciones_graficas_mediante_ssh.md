---
title: "error al Inicar aplicaciones graficas mediante ssh con xming en win"
date: 2009-02-19
forum: Software
---

### Post by dhcancelo on 2009-02-19
Buenas, consulto por si alguien tiene alguna idea sobre esto, ya que por lo leido me deberia funcionar como está.

Cuando inicio sesion con ssh, mediante putty con el X11 forwarding enable activado,
me sale esta linea antes del prompt:
/usr/bin/X11/xauth:  /home/wex/.Xauthority not writable, changes will be ignored

Using username "wex".
Authenticating with public key "imported-openssh-key"
Linux wex-desktop 2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64
Last login: Thu Feb 19 07:24:56 2009 from host170.190-30-105.telecom.net.ar
/usr/bin/X11/xauth:  /home/wex/.Xauthority not writable, changes will be ignored
wex@wex-desktop:~$

El archivo pertenece a root....
-rw------- 1 root root 122 2009-01-14 12:59 .Xauthority

Si inicio por la shell por ej el gnome-commander o el xclock para verlo aca (win XP de mi trabjo) con el serverX xming me sale esto:
wex@wex-desktop:~$ gnome-commander
PuTTY X11 proxy: wrong authentication protocol attempted
(gnome-commander:4090): Gtk-WARNING **: cannot open display: localhost:10.0

¿Tendre que adueñarme del .Xauthority y darme permiso de escritura?
Aclaro que en el sshd_config agregue la linea X11Forwarding yes y estoy usando hardy de 64 bits.

Muchas gracias po rtodo.
saludos.
wex

---

### Post by Hei Ku on 2009-02-19
Por los posts que encontré, en esos casos te conviene borrar el archivo, y lo va a regenerar la proxima vez q entres.

---

### Post by dhcancelo on 2009-02-20
Muchas gracias.
Probe con lo que me dijiste y anduvo barbaro!!
Saludos

---

### Post by dhcancelo on 2009-02-20
borre .Xauthority y el reinicar anduvo bien. Gracias

---


---
title: "error recurrente  evolution-alarm-notify"
date: 2009-11-07
forum: Software
---

### Post by granjero on 2009-11-07
bueno gente, acá con más problemas....  desde hoy empezó a aparecer una ventanita con este error. aparece cada 25 minutos mas o menos..... no uso evolution en lo más mínimo. una vez quise configurar mi gmail ahí pero después lo dejé... 

Ha ocurrido un error mientras cargaba o guardaba la información de configuración de evolution-alarm-notify. Puede que alguno de sus ajustes de configuración no funcione adecuadamente.

Falló al contactar con el servidor de configuraciones; algunas de las posibles causas son que necesite activar TCP/IP en ORBit, o que tiene bloqueos de NFS debidos a una caída de sistema. Consulte [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) para más información. (Detalles -  1: Falló al obtener la conexión con la sesión: Failed to connect to socket /tmp/dbus-8TNODrS6ZJ: Conexión rechazada)
Falló al contactar con el servidor de configuraciones; algunas de las posibles causas son que necesite activar TCP/IP en ORBit, o que tiene bloqueos de NFS debidos a una caída de sistema. Consulte [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) para más información. (Detalles -  1: Falló al obtener la conexión con la sesión: Failed to connect to socket /tmp/dbus-8TNODrS6ZJ: Conexión rechazada)

también les dejo la captura de pantalla...

---

### Post by granjero on 2009-11-07
creo que lo solucioné!

hay un archivo 
 
/etc/xdg/autostart/evolution-alarm-notify.desktop 

al cual le cambié el nombre por evolution-alarm-notify.desktop-backup

cerré la sesión y volví a abrirla... y no apareció mas el error...

si hoy en todo el día no salta de nuevo marco como solved el hilo!

salud!

---


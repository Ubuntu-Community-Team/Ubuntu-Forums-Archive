---
title: "Asistencia remota Ubuntu 8.04 y Windows Vista o XP"
date: 2009-09-22
forum: Software
---

### Post by CarlosPND on 2009-09-22
Hola comunidad.

Tengo un problema que talvez ustedes puedan guiarme para resolverlo, necesito hacer una asistencia remota desde Ubuntu a cualquier pc de ambiente windows, he logrado hacer la conexion al contrario de Windows a Ubuntu funcionando al 100%.

He intentado con el comando en el terminal:
vncviewer "IP de PC a tomar asistencia remota", pero con todo resultado fallido.

Cualquier ayuda seria de bastante agradecimiento.

Saludos

---

### Post by sergiom99 on 2009-09-23
Lo primero que tenes que asegurarte es que la PC remota tenga el servicio VNC corriendo, aceptando conexiones y el Firewall tenga el puerto necesario abierto.

Desde la consola podes poner 
```
vncviewer IP.REMOTA:PUERTO
EJ> vncviewer 10.0.2.2:4009
```

Sino, podes usar el Teamviewer con Wine, que no necesita puertos, IP, ni nada. Arrancas un exe en la maquina de XP, te pasan una clave y con el mismo EXE en Ubuntu corriendolo con Wine te conectas de una, sin firewalls ni nada.

---

### Post by deafters on 2009-09-23
Hola, mira yo uso el visor de escritorio remoto que viene de manera predeterminada cuando instalas ubuntu con gnome, y anda sin problemas, para instalarlo ? sudo apt-get install vinagre
Espero te sirva

---


---
title: "messenger no se conecta atraves de una conexion compartida"
date: 2011-11-14
forum: Software
---

### Post by Caikaku on 2011-11-14
Hola, tengo ubuntu 11.10 y comparto conexion via eth0 y eth1 seteando "compartida con otros equipos" a una pc con win7, todo funciona perfecto... Excepto que desde la pc con windows 7 no puedo conectarme al messenger, probe conectado la pc con win7 directamente al modem y ahi si pude conectarme a messenger, que puede ser?

---

### Post by hictio on 2011-11-14
Tiene un firewall activo la máquina con Ubuntu? A través de la misma y desde la máquina con Windows 7 te podés conectar a otros servicios o sólo estás navegando por internet?
El Messenger usa (como mímimo) el puerto 1863 TCP, deberías chequear si tiene un firewall activo que permita la salida por ese puerto hacia cualquier destino.
[Network ports and URLs that are used by Windows Live Messenger](http://support.microsoft.com/kb/927847)

---

### Post by guillermolisi on 2011-11-14
Por defecto, en general los sistemas GNU/Linux abren los ports de servicios desde dentro de la LAN y permiten las conexiones asi generadas. Los demas puertos, aun aquellos accesorios al principal que requiera una aplicacion, estan cerrados.

Esto puede modificarse con una interface que permita alterar la reglas de iptables (UFW, FireStarter, Shorewall, etc.) o directamente con las ordenes primitivas que modifican iptables (en linea de comandos).

En este caso puede ser que el port de MSN este abierto pero si la respuesta vuelve por otro distinto, nunca va a llegar y puede ser que por eso no termine nunca de conectar.

---


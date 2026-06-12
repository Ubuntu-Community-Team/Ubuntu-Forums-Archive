---
title: "Ayuda compartir internet entre Ubuntu y Win XP"
date: 2010-08-22
forum: Software
---

### Post by nicobr1 on 2010-08-22
Hola... Necesito ayuda con lo siguiente... Tengo dos computadoras en LAN, una esta conectada directamente a internet y a travez de la red comparte internet con la otra... En la maquina host tengo instalado ubuntu 10.04 y Windows 7 y en la otra maquina xp... desde windows 7 puedo compartir internet perfectamente con una ip dinamica pero desde ubuntu solo puedo hacerlo con una ip estatica... necesito ayuda para poder compartir internet desde ubuntu a xp con ip dinamica o alguna otra solucion que permita que desde los dos sistemas operativos pueda compartir internet sin tener que estar cambiando la ip de la maquina con xp de dinamica a estatica y viceversa... gracias

---

### Post by biale on 2010-08-24
Tendrías que instalar el paquete dhcp3-server y tocar a mano el archivo de configuracion (/etc/dhcp3/dhcpd.conf) con los parámetros de tu subred.

---


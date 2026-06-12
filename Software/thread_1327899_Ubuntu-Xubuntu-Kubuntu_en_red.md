---
title: "Ubuntu-Xubuntu-Kubuntu en red"
date: 2009-11-15
forum: Software
---

### Post by benja22 on 2009-11-15
Hola, les escribo porque tenía en casa 2 PC's más un Note, y todos con Win...
winxp, win2k y win7. La cosa es que tenía hace unos meses el CD de Ubuntu, y ahora recién me llegó Kubuntu.

Mi hno, lo uso como LiveCD en el note y le gustó. Así que era hora de la migración Y...

Ahora en el PC grande tengo Ubuntu, en el otro PC (más lento de todos) Xubuntu y en el note, que es el más rápido con Kubuntu.

Todo funciona de maravilla! Ahora estyo armando la red para compartir archivos.
Pero antes de eso, el único problema que tuve fue hacer el puente de red, Dónde Ubuntu se conectaba a internet (wlan0) y por eth0 y eth1 daba internet a Xubuntu y Kubuntu...

Les pongo como hacerlo, porque pasé milenios intentándolo... (con explicación simple para que todos puedan hacerlo!)

En ubuntu el editor de texto en administrador: sudo gedit ARCHIVO

En Kubuntu el editor de texto en administrador: kdesudo kate ARCHIVO

En Xubuntu bajen el gedit y lo hacen igual que en Ubuntu.

PRIMERO INSTALAR BRIDGE-UTILS        sudo apt-get install bridge-utils

1) Crear con SUDO un archivo en /etc/init.d llamado "puente"
Abrimos la terminal...
> cd ..
cd ..
cd etc
cd init.d
sudo gedit puente2) br0 será el puente, wlan0 es donde llega la internet y eth0 y eth1 son las 2 tarjetas para el puente

PEGAR EN EL ARCHIVO

> #!/bin/bash

#Creacion del Puente
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1
ifconfig eth0 down
ifconfig eth1 down
ifconfig eth0 0.0.0.0 up
ifconfig eth1 0.0.0.0 up
ifconfig br0 192.168.0.1 netmask 255.255.255.0 up
route add default gateway 192.168.0.1

#Compartiendo internet
iptables --flush
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i br0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward3) Cerramos el archivo y le damos permiso de ejecutar
> sudo chmod +x puente4) Lo agregamos para que se ejecute al inicio:

> sudo update-rc.d puente defaults
5) Reiniciar y OK

6) Asignar IP en otros PC's
IP: 192.168.0.X  no usar 1
MAscara: 255.255.255.0
Gateway: 192.168.0.1
DNS: Algun DNS de internet... como OpenDNS 208.67.222.222

---

### Post by Carlos C on 2009-11-15
Movido a "software". Recordar publicar en el subforo [adecuado]("http://ubuntuforums.org/showthread.php?t=1319475").

De todas maneras, gracias por el aporte. ;)

Saludos!

---


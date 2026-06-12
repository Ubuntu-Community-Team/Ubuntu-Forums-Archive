---
title: "Gnome se cuelga a la 1ra vez!"
date: 2009-06-10
forum: Software
---

### Post by Mauro22 on 2009-06-10
Hola!!


Tiro el problema aca porque en el IRC mucho no pudimos hacer. A parte quedo descartado el hardware, asi que solo lo puedo insultar.


La cosa e' mas o menos asi:


Prendo la notebook, llegamos al GDM, inicio sesión y carga gnome y compiz. Todo bien hasta ahi.

Abro lo que sea (lease opera, emesene, nautilus, menu, etc etc) y se cuelga todo excepto el mouse:

* No puedo hacer control alt F1 (no lo toma)
* No puedo hacer control alt backspace (no lo toma)
* Boton (fisico) del power (no lo toma)
* Lo unico que funca es alt + impr pant + R E I S U B

Luego de ejecutar el REISUB, reinicia, vuelvo al gdm, entro a gnome y wow! anda todo un lujo.. anda de 11! 

Esto es asi siempre con gnome. la primera vez que la prendo se cuelga, despues del reincio no.



Descarte hardware por:

* Probe con kde, openbox, fluxbox y no pasa
* Probe con gnome pero sin compiz y sigue pasando
* Probe con fedora (y compiz) y no pasa
* Probe con V*sta y no pasa

Les dejo el lspci para quien lo necesite.
```
mauro@mauro-acer:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```


Cualquier otra cosa, pidan nomas..




Pistas: 
* Al instalar 9.04 32 bits no lo hizo nunca. Lo empezo a hacer hará un 1 mes por ahi.
* Uso Ext 4 en el formateo
* Actualizado al dia
* Pasa con bateria y estando conectada a AC

Espero que juntos podamos resolverlo, porque de verdad me encanta gnome (sin ofender a los KDEististas) y rompe las b*l*s tener que reiniciar para poder usar.

Ahi les van unos pochoclos por la buena onda:
:popcorn:

---

### Post by staar on 2009-06-10
y reiniciando las configuraciones de gnome a las default? con ```
gconftool-2 --recursive-unset /
``` OJO, que, si usas network-manager, también reinicia las configuraciones de red...

o creando un nuevo usuario?

saludos

---

### Post by Mister X on 2009-06-10
yo probaria creando un nuevo usuario, y viendo que pasa con la config pelada

y estaria piola si podes probar de conectarte por ssh desde otra maquina cuando la tuya se bloquea, y así mirar si hay algun proceso desbocado o algo raro

---

### Post by Mauro22 on 2009-06-10
Antes que nada, gracias por la respuestas

@staar, @Mister X

Lamentablemente no puedo probar sus soluciones, de bo*****o nomas entre a toquetear y no arrancó más...


Asi que bue.. ahora instalé fedora 11 que salió ayer y con compiz y todo eso no hay problemas!


Si instalo Ubuntu de nuevo y da ese error de una, revivo el post!



Gracias!!
[SOLVED] por ahora

---

### Post by Mauro22 on 2009-06-28
Bueno, tras reinstalar Ubuntu de nuevo, a los pocos dias, volvió a hacer la misma falla.

Al parecer Ubuntu JJ pone a las placas Intel en la blacklist por lo que sumandole Compiz puede resultar en el apocalipsis.

Buscando en internet, llegué a la conclusión de que el error lo produce el driver de la placa de video de Intel que trae JJ, pero no lo hace con el que usa II, por lo tanto, esta mini guia, nos permite instlar dicho driver.

Dejo los pasos, sacados de aqui [0]

Agregar a /etc/apt/sources.list: 

```
deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Importar la llave GPG: 

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79
```

Instalar el driver:

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel-2.4
```

Reiniciar la X:

```
sudo /etc/init.d/gdm restart
```


_**Si no funciona o quedó peor, hay que hacer un *rollback*:**_

Borrar las entradas de /etc/apt/sources.list que agregamos anteriormente.

Instalar el driver que viene con 9.04:

```
sudo apt-get install xserver-xorg-video-intel
```

Reiniciar la X:

```
sudo /etc/init.d/gdm restart
```

[0] [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

PD: En [0] pueden encontrar rev por rev de las placas, cuales traen problemas y cuales no.


Esto es todo. Si tienen una Intel Graphics y JJ anda mal, prueben esto!!

A mi me salvó y ahora JJ no se cuelga :D

---


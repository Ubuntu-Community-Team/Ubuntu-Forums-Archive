---
title: "Kubuntu Karmic consume todos los recurso de la notebook"
date: 2010-02-18
forum: Software
---

### Post by jandry on 2010-02-18
Amigos del foro, les cuento que luego de la actualizacion a Karmic empezaron los problemas con mi notebook, se congela el mouse y las aplicaciones, tipeo en consola top y me muestra que Xorg consume el 94% de cpu Esto no me pasa en gnome ni en xfce por lo que deduzco que tiene que ver con la version de KDE, como no pienso renunciar a mi querido KDE espero que alguien me oriente en la solucion del problema. Cualquier sugerencia es mas que bienvenida.
Abrazo Ubuntero
Alejandro

---

### Post by juancarlospaco on 2010-02-19
Actualiza/reinstala el Xorg,* habia un muy viejo ug que hacia que consuma el CPU.*

---

### Post by guillermolisi on 2010-02-19
Jandry

Tenes actualizada al dia esa maquina con Kubuntu ? Mira que en las ultimas dos semanas hubo una tormenta de paquetes nuevos entre los de seguridad, mejoras y nuevas versiones, entre ellas KDE 4.4.

---

### Post by jandry on 2010-02-21
Guille, tengo todo al dia, la verdad no se que hacer,estoy perdido, de ultima en la primera reunion llevo la maquina y las vemos entre todos los kdeeros...
No estoy seguro de reinstalar Xorg ya que con losotros escritorios anda todo bien. Sigo googleando pero todavia nada.
Abrazo ubuntero
Alejandro

---

### Post by guillermolisi on 2010-02-21
> **jandry said:**
> Guille, tengo todo al dia, la verdad no se que hacer,estoy perdido, de ultima en la primera reunion llevo la maquina y las vemos entre todos los kdeeros...
No estoy seguro de reinstalar Xorg ya que con losotros escritorios anda todo bien. Sigo googleando pero todavia nada.
Abrazo ubuntero
Alejandro
Que te dice "top" ? O si queres "stop" ?

---

### Post by alfplayer on 2010-02-21
> **guillermolisi said:**
> Que te dice "top" ? O si queres "stop" ?

stop es un comando de Upstart. Un muy buen comando tipo "top" es "htop".

---

### Post by guillermolisi on 2010-02-21
> **alfplayer said:**
> stop es un comando de Upstart. Un muy buen comando tipo "top" es "htop".
Pufffff !!! Impresionante mi furcio !!!

Gracias Alfaplayer por la necesaria y bien hecha correccion y aclaracion !!

Disculpen, mucha humedad parece que me afecto :) , "htop"  es la alternativa que quise mencionar.

---

### Post by jandry on 2010-02-22
En el momento del "fallo", lo unico significativo en top es la columna de %CPU pasa de 3% a 50% y en algunos casos a 94%.
Abrazo ubuntero
Alejandro

---

### Post by guillermolisi on 2010-02-22
> **jandry said:**
> En el momento del "fallo", lo unico significativo en top es la columna de %CPU pasa de 3% a 50% y en algunos casos a 94%.
Abrazo ubuntero
Alejandro
Ok, y el resto de las columnas, principalmente la que menciona que proceso se lleva toda esa cantidad de CPU menciona indefectiblemente a Xorg o hay alguna otra como Plasma, etc ?

De paso, que placa de video estas usando (marca y modelo) ?
Tenes configurado algo en /etc/X11/xorg.conf ? Si es asi, podrias mostrar su contenido ?

---

### Post by jandry on 2010-02-23
Aca van los datos:

jandry@jandry-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
05:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
06:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:04.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

y aqui xorg.conf

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

en cuanto a top, si, especificamente Xorg es loa que consume todos las recursos.
Gracias por su infinita paciencia.
Abrazo ubuntero

PD: en el FLISOL yo invito las cervezas Gille.

---

### Post by guillermolisi on 2010-02-23
Lo primero que veo y que no me gusta nada es que esa maquina (lamentablemente) tiene video VIA.
Luego, tenes idea que driver de video estas usando ? Porque los Unichrome y equivalentes, propietarios de VIA inclusive, no funcionan y he leido y sufrido (dos maquinas con ese chip de video) que los que los han utilizado les fue peor que con el generico VESA.

Algo me dice que si le pones una placa de video decente, una nVidia y/o ATI (soportadas por Ubuntu) te sacas este problema de encima. Si no estas usando driver VESA, probaria primero eso configurando en el /etc/X11/xorg.conf las frecuencias de barrido vertical y horizontal del monitor, las resoluciones y algun otro dato que tenga que ver con las caracteristicas del video.

En mi maquina de la oficina tengo aun copias del contenido de ese archivo cuando usaba la PC con la placa VIA y driver VESA. Si queres probar, avisame y te los paso para que los tomes de ejemplo y veas que efecto tienen en tu caso.

---


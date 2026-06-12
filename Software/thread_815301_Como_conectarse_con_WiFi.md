---
title: "Como conectarse con WiFi"
date: 2008-06-01
forum: Software
---

### Post by germanfk on 2008-06-01
Hola amigos UBUNTEROS!!, desde Posadas Misiones los saludos y planteo una duda, para quien pueda responderme...
2x1
Una pregunta es como confiurar el adaptador usb para WiFi ENUWI-G2. Estuve siguiendo un par de tutoriales donde recomienda que instale el driver para Win98, pero... soy nuevo en estas tierras, asi que aun no di en el clavo!

Otra pregunta dentro del ramo... para una Notebook Toshiba Satellite P205-s6348 como se configura la conexión WiFi tambien. El dispositivo (lease lucecita) se enciende, por lo que deduzco que está instlada... :confused:

Por ultimo por mas que cuesta un poco al principio... que grande Ubuntu!! viva linux...

Nos leemos pronto.

---

### Post by faktorqm on 2008-06-01
Hola, bienvenido al foro. La guia que funciona, es esta: [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958) y si no sabés inglés, vamos a estar muy contentos de traducirla para que puedas seguirla. 

Éste tiene 2 años :S pero esta en castellano. Si no tenés mucha idea tal vez solo lo puedas tener como referencia... [http://delajusco.wordpress.com/2007/10/10/como-instalar-un-adaptador-wifi-encore-enuwi-g2-en-ubuntu-610-edgy-eft/](http://delajusco.wordpress.com/2007/10/10/como-instalar-un-adaptador-wifi-encore-enuwi-g2-en-ubuntu-610-edgy-eft/)

Por favor posteá la salida del comando "lspci" (sin comillas) y "lsusb" (sin comillas) para ver de que dispositivo estamos hablando, vi que habia 2 modelos, 8187L y 8187M.

Lo de la toshiba lo vemos despues.... XD Salu2!

---

### Post by germanfk on 2008-06-01
Gracias amigo por la bienvenida y las pautas para reconocer el problema.
Hice la tarea, te paso.

**Con lspci**

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

**y con lsusb**

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

No se si se pasa así... pero me fue lo mas práctico por ahora!
Te leo!

---

### Post by faktorqm on 2008-06-01
ammm me da la sensacion de que no ejecutaste los comandos con la placa de red enchufada... estoy en lo cierto? sino ubuntu ni siquiera la "ve"...

ahh y por favor, cada vez que postees una salida, apreta el simbolo numeral (#) que ves en las heramientas del mensaje para mejor ordenamiento del foro. Gracias y saludos!!

---


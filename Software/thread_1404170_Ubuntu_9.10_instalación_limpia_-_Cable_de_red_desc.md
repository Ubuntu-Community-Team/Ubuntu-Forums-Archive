---
title: "Ubuntu 9.10 instalación limpia - Cable de red desconectado"
date: 2010-02-11
forum: Software
---

### Post by lufe on 2010-02-11
Hola chicos. Consulté a un moderador antes de publicar este post porque como soy de Uruguay no de Argentina no sabía si podía hacer una pregunta aquí.


Tengo un problema que intenté resolver buscando información por todos lados, e incluso posteando en este foro: [http://www.ubuntu-es.org/?q=node/127500](http://www.ubuntu-es.org/?q=node/127500) donde un chico amablemente me ayudó pero aún así no lo pude resolver. Por eso recurro a este foro.


  Al grano, miren, tenía Ubuntu 7 y funcionaba perfecto instalado junto con Windows XP.
 

Ayer decidí instalar Ubuntu 9.10 desde cero pero una vez instalado me dice que el cable de red está desconectado lo cual no es cierto. Tampoco es problema del cable o del modem porque en la misma computadora en XP funciona todo bien.
 

Probé desde el Live CD de Ubuntu 9.10 directamente y tampoco tuve suerte.



Es un tema de drivers o algo que me falta hacer? Lo raro es que cuando instalé Ubuntu 7 nunca precisé hacer nada especial, lo instalé configuré la conexión y listo.
 

Gracias por la ayuda, estoy trancada y la verdad que me gustaría poder usar Ubuntu 9.

---

### Post by guillermolisi on 2010-02-11
Para poder aconsejarte, pasanos la salida de los comandos "lspci" y "lshw" (sin las comillas) ejecutado en una consola/terminal. Lo que nos interesa saber es que y como detecta Ubuntu tu placa de red (network adapter).
Ahi veremos si la placa esta adecuadamente reconocida para pasar al proximo paso que seria configurar la conexion de red, ya sea via NetworkManager o "a mano".

---

### Post by lufe on 2010-02-11
Gracias Guillemo.

[SIZE=5]**LSPCI**[/SIZE]
   lufe@lufe-ubuntu:~$ lspci
  
  00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
  
  00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
  
  00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
  
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
  
  00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  
  00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  
  00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  
  00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
  
  01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
  
  lufe@lufe-ubuntu:~$ ^C
  
  lufe@lufe-ubuntu:~$ 
  
  
-----------------------------------------------------------------------------------------------------

**[SIZE=5]LSHW[/SIZE]**
   lufe@lufe-ubuntu:~$ lshw
  
  WARNING: you should run this program as super-user.
  
  lufe-ubuntu            
  
      description: Computer
  
      width: 32 bits
  
    *-core
  
         description: Motherboard
  
         physical id: 0
  
       *-memory
  
            description: System memory
  
            physical id: 0
  
            size: 938MiB
  
       *-cpu
  
            product: AMD Sempron(tm) Processor 2800+
  
            vendor: Advanced Micro Devices [AMD]
  
            physical id: 1
  
            bus info: cpu@0
  
            version: 15.12.2
  
            size: 1600MHz
  
            width: 64 bits
  
            capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm
  
          *-cache:0
  
               description: L1 cache
  
               physical id: 0
  
               size: 128KiB
  
          *-cache:1
  
               description: L2 cache
  
               physical id: 1
  
               size: 256KiB
  
       *-pci:0
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 100
  
            bus info: pci@0000:00:00.0
  
            version: 00
  
            width: 32 bits
  
            clock: 66MHz
  
            configuration: driver=agpgart-amd64 latency=8
  
            resources: irq:0 memory:f8000000-fbffffff(prefetchable)
  
          *-pci
  
               description: PCI bridge
  
               product: VT8237 PCI bridge [K8T800/K8T890 South]
  
               vendor: VIA Technologies, Inc.
  
               physical id: 1
  
               bus info: pci@0000:00:01.0
  
               version: 00
  
               width: 32 bits
  
               clock: 66MHz
  
               capabilities: pci bus_master cap_list
  
               resources: memory:fca00000-feafffff memory:eff00000-f7efffff(prefetchable)
  
             *-display UNCLAIMED
  
                  description: VGA compatible controller
  
                  product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
  
                  vendor: VIA Technologies, Inc.
  
                  physical id: 0
  
                  bus info: pci@0000:01:00.0
  
                  version: 01
  
                  width: 32 bits
  
                  clock: 66MHz
  
                  capabilities: bus_master cap_list
  
                  configuration: latency=32 mingnt=2
  
                  resources: memory:f0000000-f3ffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)
  
          *-storage
  
               description: RAID bus controller
  
               product: VIA VT6420 SATA RAID Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: f
  
               bus info: pci@0000:00:0f.0
  
               version: 80
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: storage bus_master cap_list
  
               configuration: driver=sata_via latency=32
  
               resources: irq:20 ioport:ec00(size=8) ioport:e800(size=4) ioport:e400(size=8) ioport:e000(size=4) ioport:dc00(size=16) ioport:d800(size=256)
  
          *-ide
  
               description: IDE interface
  
               product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
  
               vendor: VIA Technologies, Inc.
  
               physical id: f.1
  
               bus info: pci@0000:00:0f.1
  
               version: 06
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: ide bus_master cap_list
  
               configuration: driver=pata_via latency=32
  
               resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
  
          *-usb:0
  
               description: USB Controller
  
               product: VT82xxxxx UHCI USB 1.1 Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 10
  
               bus info: pci@0000:00:10.0
  
               version: 81
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list
  
               configuration: driver=uhci_hcd latency=32
  
               resources: irq:21 ioport:bc00(size=32)
  
          *-usb:1
  
               description: USB Controller
  
               product: VT82xxxxx UHCI USB 1.1 Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 10.1
  
               bus info: pci@0000:00:10.1
  
               version: 81
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list
  
               configuration: driver=uhci_hcd latency=32
  
               resources: irq:21 ioport:c000(size=32)
  
          *-usb:2
  
               description: USB Controller
  
               product: VT82xxxxx UHCI USB 1.1 Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 10.2
  
               bus info: pci@0000:00:10.2
  
               version: 81
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list
  
               configuration: driver=uhci_hcd latency=32
  
               resources: irq:21 ioport:c400(size=32)
  
          *-usb:3
  
               description: USB Controller
  
               product: VT82xxxxx UHCI USB 1.1 Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 10.3
  
               bus info: pci@0000:00:10.3
  
               version: 81
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list
  
               configuration: driver=uhci_hcd latency=32
  
               resources: irq:21 ioport:cc00(size=32)
  
          *-usb:4
  
               description: USB Controller
  
               product: USB 2.0
  
               vendor: VIA Technologies, Inc.
  
               physical id: 10.4
  
               bus info: pci@0000:00:10.4
  
               version: 86
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list
  
               configuration: driver=ehci_hcd latency=32
  
               resources: irq:21 memory:febff800-febff8ff
  
          *-isa
  
               description: ISA bridge
  
               product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
  
               vendor: VIA Technologies, Inc.
  
               physical id: 11
  
               bus info: pci@0000:00:11.0
  
               version: 00
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: isa bus_master cap_list
  
               configuration: latency=0
  
          *-multimedia
  
               description: Multimedia audio controller
  
               product: VT8233/A/8235/8237 AC97 Audio Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 11.5
  
               bus info: pci@0000:00:11.5
  
               version: 60
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: cap_list
  
               configuration: driver=VIA 82xx Audio latency=0
  
               resources: irq:22 ioport:c800(size=256)
  
          *-communication
  
               description: Communication controller
  
               product: AC'97 Modem Controller
  
               vendor: VIA Technologies, Inc.
  
               physical id: 11.6
  
               bus info: pci@0000:00:11.6
  
               version: 80
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: cap_list
  
               configuration: driver=VIA 82xx Modem latency=0
  
               resources: irq:22 ioport:d000(size=256)
  
          *-network
  
               description: Ethernet interface
  
               product: VT6102 [Rhine-II]
  
               vendor: VIA Technologies, Inc.
  
               physical id: 12
  
               bus info: pci@0000:00:12.0
  
               logical name: eth0
  
               version: 78
  
               serial: 00:13:8f:7a:b4:60
  
               width: 32 bits
  
               clock: 33MHz
  
               capabilities: bus_master cap_list ethernet physical
  
               configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 multicast=yes
  
               resources: irq:23 ioport:d400(size=256) memory:febffc00-febffcff
  
       *-pci:1
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 101
  
            bus info: pci@0000:00:00.1
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:2
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 102
  
            bus info: pci@0000:00:00.2
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:3
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 103
  
            bus info: pci@0000:00:00.3
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:4
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 104
  
            bus info: pci@0000:00:00.4
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:5
  
            description: Host bridge
  
            product: K8M800 Host Bridge
  
            vendor: VIA Technologies, Inc.
  
            physical id: 105
  
            bus info: pci@0000:00:00.7
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:6
  
            description: Host bridge
  
            product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  
            vendor: Advanced Micro Devices [AMD]
  
            physical id: 106
  
            bus info: pci@0000:00:18.0
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:7
  
            description: Host bridge
  
            product: K8 [Athlon64/Opteron] Address Map
  
            vendor: Advanced Micro Devices [AMD]
  
            physical id: 107
  
            bus info: pci@0000:00:18.1
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:8
  
            description: Host bridge
  
            product: K8 [Athlon64/Opteron] DRAM Controller
  
            vendor: Advanced Micro Devices [AMD]
  
            physical id: 108
  
            bus info: pci@0000:00:18.2
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
       *-pci:9
  
            description: Host bridge
  
            product: K8 [Athlon64/Opteron] Miscellaneous Control
  
            vendor: Advanced Micro Devices [AMD]
  
            physical id: 109
  
            bus info: pci@0000:00:18.3
  
            version: 00
  
            width: 32 bits
  
            clock: 33MHz
  
            configuration: driver=k8temp
  
            resources: irq:0
  
  lufe@lufe-ubuntu:~$ ^C
  
  lufe@lufe-ubuntu:~$

---

### Post by guillermolisi on 2010-02-11
Esa placa de red deberia salir funcionando al toque. De hecho la estoy usando en varias maquinas que tienen motherboard Asus.

Con esa placa te conectas al modem que te da la conexion a Internet o a algun otro dispositivo ?

---

### Post by lufe on 2010-02-11
Hola, con esa placa lo conecto al modem del ADSL.

En Windows XP e incluso en Ubuntu CD Live 7.0 o 8.10 me funciona correctamente, digo, me deja conectarme sin drama.

El problema me lo da Ubuntu 9.10.

Qué podrá ser?

---

### Post by santiago79 on 2010-02-11
te fijaste poniendo las conexiones malamente poniendo una ip mascara puerta de enlace y dns?
tu módem lo routiaste?  
proba eso ponerlo en modo router y configurarlo manualmente no automático

---

### Post by lufe on 2010-02-11
> **santiago79 said:**
> te fijaste poniendo las conexiones malamente poniendo una ip mascara puerta de enlace y dns?
tu módem lo routiaste?  
proba eso ponerlo en modo router y configurarlo manualmente no automático

Santiago no tengo ni idea de como hacer todo eso... :( voy a ver que puedo investigar.

Lo que se es que con Ubuntu 7 y Ubuntu 8.10 me funcionaba todo sin problemas.

Voy a ver que puedo hacer, gracias por la ayuda.

---

### Post by guillermolisi on 2010-02-11
El post de Edgar fue [movido]("http://ubuntuforums.org/showthread.php?t=1404742") a la seccion Comunidad ya que no era exactamente el mismo topico que el thread en curso.

El post sobre el error al inicio del sistema tambien fue [movido]("http://ubuntuforums.org/showthread.php?t=1404740") pero en la seccion Software.

Por favor, mantenerse en tema asi no se desvirtuan los hilos propuestos. Gracias

---

### Post by guillermolisi on 2010-02-11
> **lufe said:**
> Santiago no tengo ni idea de como hacer todo eso... :( voy a ver que puedo investigar.

Lo que se es que con Ubuntu 7 y Ubuntu 8.10 me funcionaba todo sin problemas.

Voy a ver que puedo hacer, gracias por la ayuda.
Antes de tocar algun archivo, podrias mostrarnos el contenido de /etc/network/interfaces ?

---

### Post by lufe on 2010-02-12
Esto es lo que contiene el archivo interfaces

auto lo
iface lo inet loopback

---

### Post by santiago79 on 2010-02-12
> **lufe said:**
> Santiago no tengo ni idea de como hacer todo eso... :( voy a ver que puedo investigar.

Lo que se es que con Ubuntu 7 y Ubuntu 8.10 me funcionaba todo sin problemas.

Voy a ver que puedo hacer, gracias por la ayuda.

bueno fíjate que módem tenes y decinos y vos cuando te conectas en windows xp apenas la prendes ya esta conectada a internet o tenes que discar vos a mano?

---

### Post by guillermolisi on 2010-02-12
> **lufe said:**
> Esto es lo que contiene el archivo interfaces

auto lo
iface lo inet loopback
Ok, en una consola/terminal edita el archivo /etc/network/interfaces usando algun editor de texto tipo nano: ```
sudo nano /etc/network/interfaces
```Agregale estas lineas debajo de las que nos mostraste: ```
iface eth0 inet dhcp
auto eth0
```El archivo en cuestion deberia quedar asi:
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```Salva las modificaciones e ingresa en linea de comando lo siguiente: ```
sudo /etc/init.d/networking restart
``` para reiniciar el servicio de red para que tome las modificaciones introducidas. Todo esto con el cable de red conectado a esa placa integrada.
Proba si tenes conexion y contanos como te fue.

---

### Post by lufe on 2010-02-12
Hola Guillermo hice lo que me indicaste.

Al terminar los comandos en el terminal salió esto:

```
lufe@lufe-ubuntu:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.2

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/eth0/00:13:8f:7a:b4:60

Sending on   LPF/eth0/00:13:8f:7a:b4:60

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

grep: /etc/resolv.conf: No such file or directory

                                                                         [ OK ]

lufe@lufe-ubuntu:~$ 
```Probé la conexión y seguía sin poder conectarme, lo más raro es que al reiniciar Ubuntu ya no me aparecía mi conexión de DSL así que intenté configurarla de nuevo... y no me deja, me permite entrar y poner los datos pero cuando doy AÑADIR la ventana se cierra y no me guarda nada, como si no tuviera permisos a algo.

En conexiones de red cableada me sale esto que antes no estaba

[IMG]http://img22.imageshack.us/img22/2382/pantallazoconexionesder.png[/IMG]

---

### Post by guillermolisi on 2010-02-12
Ok, edita el archivo nuevamente y borra el bloque agregado asi recuperas la entrada de conexion DSL en el Network Manager.

El router ADSL que estas usando esta en modo router o en modo bridge ? Si tenes que conectar discando antes esta en modo Bridge (que es lo que creo). Si esta en modo Router se conecta solo sin mas tramite.

Si estuviera en modo Router la prueba que hiciste deberia haber encontrado un servidor DHCP para tomar una IP dinamica provista por tu ISP, cosa que no sucedio.

---

### Post by lufe on 2010-02-13
Hola Guillermo, creo que está en modo Bridge. Al menos en Windows XP inicio sesión y debo hacer doble clic en el icono de conexión para que disque y se conecte al ADSL.

Reestablezco el archivo a como estaba antes y qué más debo hacer?

---

### Post by guillermolisi on 2010-02-14
> **lufe said:**
> Hola Guillermo, creo que está en modo Bridge. Al menos en Windows XP inicio sesión y debo hacer doble clic en el icono de conexión para que disque y se conecte al ADSL.

Reestablezco el archivo a como estaba antes y qué más debo hacer?
Si, esta en modo Bridge y desde mi punto de vista lo mas saludable seria pasarlo a modo Router.

En caso de que lo dejes en modo Bridge hay que configurar el discador para pppoe y activarlo antes de iniciar el uso de Internet (tal como haces en Win).

En todo caso, deja el archivo que modificaste como estaba originalmente y volvemos a empezar pero con pppoe.

Dale una leida a estos threads:

[http://ubuntuforums.org/showthread.php?t=1312572](http://ubuntuforums.org/showthread.php?t=1312572)
[http://ubuntuforums.org/showthread.php?t=1370869](http://ubuntuforums.org/showthread.php?t=1370869)

---

### Post by lufe on 2010-02-15
Hola Guillermo el miércoles hago la prueba y aviso acá mismo en este hilo. 

Muchas gracias.

---

### Post by santiago79 on 2010-02-16
como te dije antes pone el modelo de módem que tenes así es mas fácil de ponerlo en modo router si es que funciona como router, aparte es mas practico y mucho mas cómodo

---

### Post by lufe on 2010-02-17
> **santiago79 said:**
> bueno fíjate que módem tenes y decinos y vos cuando te conectas en windows xp apenas la prendes ya esta conectada a internet o tenes que discar vos a mano?

Hola Santiago no te había entendido antes, perdona.

Mi Modem es Modem Speedtouch y por la foto parece ser este:

Rotear SpeedTouch 510 V6

[http://begindownload.wordpress.com/2009/07/16/rotear-speedtouch-510-v6/](http://begindownload.wordpress.com/2009/07/16/rotear-speedtouch-510-v6/)

[http://begindownload.files.wordpress.com/2009/07/modem.jpg](http://begindownload.files.wordpress.com/2009/07/modem.jpg)

---

### Post by lufe on 2010-02-17
Pude conectarme, no lo puedo creer !!!

:)

Era tan simple como ejecutar

sudo pppoeconf 

Luego le di mi usuario y contraseña y conecta sin problemas. 

En un momento el asistente me dijo esto:

[IMG]http://img220.imageshack.us/img220/1861/1preguntaquemehizoalcon.png[/IMG]


Ni idea que es pero le dije que SI y listo.

Si apago o reinicio también conecta sin pedirme nada de nuevo!

Lo que no entiendo es porqué en el panel de las conexiones de red no me aparece rastro de la configuración.

[IMG]http://img294.imageshack.us/img294/2655/2meconectaperosindsl.png[/IMG]

Supongo que se debe a que me conecté por el pppoeconf, no se, no entiendo mucho, pero al menos me puedo conectar, ahora puedo seguir aprendiendo y acostumbrándome a este nuevo Ubuntu y espero de acá a menos de un año pasarme por completo a Ubuntu.

Muchas gracias guillermo y santiago por la ayuda.

Seguiré por acá leyendo y aprendiendo.

;)

---

### Post by lufe on 2010-02-17
No me deja marcar el asunto de este hilo como resuelto, pero aviso por si algún moderador quiere hacerlo.

---

### Post by santiago79 on 2010-02-25
perdon por la tardanza pero tuve muchos problemas, me alegro que puedas conectarte, para que no te pase mas estoy trata de conseguir un router asi te salteas los dolores de cabeza como este jajajaj
saludos

---


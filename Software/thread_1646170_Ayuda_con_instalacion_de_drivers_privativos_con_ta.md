---
title: "Ayuda con instalacion de drivers privativos con tarjeta gráfica Intel"
date: 2010-12-15
forum: Software
---

### Post by teko83 on 2010-12-15
Amigos de ubuntu Chile
tengo un notebook toshiba, modelo l645-sp4004l con una placa intel.
Mi problema es que no he podido instalar los drivers de esa placa y me tiene a mal traer esto
Instalé ubuntu 10.10 y les adjunto lo que aparece en lspci


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


Ojalá puedan ayudarme
Saludos

---

### Post by Breped on 2010-12-15
Hola teko83:

No me queda del todo claro para qué querrías instalar los drivers (obviamente algo propietario) de la placa Intel. Digo, porque Ubuntu detectará todos los dispositivos con drivers OpenSource y los habilitará automáticamente.
Para aquellos dispositivos que no cumplan la regla anterior, buscará aquellos drivers propietarios que estén disponibles y te lo hará saber con un ícono (de una tarjeta de circuito impreso) en la barra de tareas.
Generalmente, las personas quieren instalar drivers propietarios para tarjetas de video o WiFi; ¿es ése tu caso? ¿Qué dispositivos de tu computador requieren de drivers propietarios para trabajar?
Al ver tu listado de hardware, me parece que el único que requiere algo especial debería ser la tarjeta Ethernet Atheros, que normalmente deben ser tratadas por separado, pero con el instalador de drivers propietarios de Ubuntu, siempre me ha resultado OK.

---

### Post by teko83 on 2010-12-16
Mi problema es con la tarjeta de video, ya que por ejemplo no puedo utilizar los efectos de compiz, por ejemplo, o la transparencia de la terminal (se ve bastante feo)

El resto de los drivers no he tenido problemas, solo el sonido que al conectarle audífonos no se escuchan y se sigue escuchando en los parlantes
Saludos

---

### Post by asterix77 on 2010-12-17
Por simple curiosidad te has ido a :

Sistema----->Administración ------>Controladores de hardware y aquí verificar si es que existe algún driver privativo para tu tarjeta?

Escribe la salida por terminal de lo siguiente:

$lspci | grep VGA

$glxinfo | grep render

Otra cosa que puedes hacer, es agregar el siguiente repositorio, para ello debes hacer lo siguiente desde la terminal:

$sudo echo "deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) maverick main" >> /etc/apt/sources.list

$sudo aptitude update

$sudo aptitude safe-upgrade

Con esto verificas si hay nuevos controladores para tu tarjeta de video; y si los hay lo instala, y si hay nuevas actualizaciones te avisa.

Si haces esto último (agregar el repositorio), pega la salida de los dos primeros comandos de nuevo para saber si ha cambiado en algo tu situación, es decir:


$lspci | grep VGA

$glxinfo | grep render


Saludos

---

### Post by teko83 on 2010-12-19
Hice lo que me dijiste, y me aparecen las siguientes cosas

francisco@pancho-note:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
francisco@pancho-note:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT x86/MMX/SSE2

Ojalá puedas ayudarme

Saludos

---

### Post by asterix77 on 2010-12-20
Mmmm, según lo que te arroja la terminal, tu tarjeta es reconocida, y además tienes aceleración gráfica. Se supone que ya con aceleración, deberías poder activar los efectos de compiz.

¿agregastes el repositorio que te indiqué?.


Para ver como te funciona la aceleración, ejecuta en la terminal lo siguiente:

$glxgears

Te van a aparecer unos engranajes dando vueltas en una ventana pequeña; dejalo funcionando lo suficiente como para reunir unos 10 datos (50 segundos más o menos), y luego maximiza la ventana y espera otros 50 segundos para reunir unos 10 datos más pero con pantalla maximizada (los datos te aparecen en la terminal), luego pega esos resultados acá. Importante: mientras ocurre ese proceso no hagas nada en tu pc.

A lo mejor tu problema no radica en la aceleración, sino en otra cosa, por eso hay que descartar.


Saludos


PD: Si tienes problemas durante la visualización de los engranajes, comenta que tipo de problema es.

---

### Post by teko83 on 2010-12-20
Instalé el repositorio que tu me habías comentado, y los resultados fueron los mostrados en el post anterior...
Ahora realizando tus nuevas instrucciones, estos son los resultados

francisco@pancho-note:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
297 frames in 5.0 seconds = 59.391 FPS
299 frames in 5.0 seconds = 59.701 FPS
299 frames in 5.0 seconds = 59.699 FPS
298 frames in 5.0 seconds = 59.496 FPS
299 frames in 5.0 seconds = 59.701 FPS
299 frames in 5.0 seconds = 59.699 FPS
299 frames in 5.0 seconds = 59.698 FPS
299 frames in 5.0 seconds = 59.695 FPS
299 frames in 5.0 seconds = 59.701 FPS
299 frames in 5.0 seconds = 59.700 FPS
294 frames in 5.0 seconds = 58.655 FPS
295 frames in 5.0 seconds = 58.904 FPS
298 frames in 5.0 seconds = 59.538 FPS
295 frames in 5.0 seconds = 58.901 FPS
295 frames in 5.0 seconds = 58.898 FPS
299 frames in 5.0 seconds = 59.698 FPS
296 frames in 5.0 seconds = 59.052 FPS
295 frames in 5.0 seconds = 58.903 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 10923 requests (10923 known processed) with 0 events remaining.


La verdad no sé que pueda ser

---

### Post by teko83 on 2010-12-20
Se me olvidaba comentarte, intenté activar los efectos y como que trata de tirarlos, pero vuelve a la pantalla normal y la pestaña de seleccion de efectos se queda pegada :S

---

### Post by moreback on 2010-12-21
Tienes aceleración pero parece que el compiz tiene tu tarjeta en alguna blacklist.

---

### Post by asterix77 on 2010-12-21
Esos casi 300 frames en 5 seg. ¿son a pantalla minimizada o a pantalla maximizada?.

Porque si es a pantalla minimizada estamos mal, ya que a mi por ejemplo me dan valores de 1100 app con pantalla minimizada; y valores cercanos a 240 con pantalla maximizada.

Otra opción que puedes hacer es ir a Sistema---->Preferencias----->Apariencias------>Efectos Visuales

Y aquí checkear extra o personalizado si es que te aparece la opción.


Sin con esto sigue igual, creo que tal vez el problema sea compiz

---

### Post by teko83 on 2010-12-22
la aceleración es con la pantalla normal y maximizada
he checkeado las opciones de apariencia, pero al cambiarla, se queda pegada las opiciones, hace el intento por cambiar y vuelve normal, eso si sin poder cerrar la ventana de apariencias, de hecho tengo que matar el proceso

---

### Post by RafaelG on 2010-12-23
[SIZE=2]Teko83,

Yo apoyo la idea que tu tarjeta esta en una blacklist y para poder habilitar los efecto podrias sacar la tarjeta de video de la blacklist. para eso te recomiendo abrir una terminal y ingresar lo siguiente "gksudo nautilus" despues buscar la carpeta etc/modprobe.d/blacklist.conf y sacar "#" en la linea que aparece tu tarjeta. guardar y cerrar. Despues deberias poder habilitar los efectos compiz.

Para terminar la idea se supone que cuando un hardware esta en Blacklist es por que en la pruebas realizadas por Ubuntu ha presentado alguna inestabilidad o inconveniente con el driver por lo que deshabilitan el Hardware momentaniamente ingresandolo a una Blacklist hasta que pueda normalisar el problema y en una de tantas actualizaciones deberia venir la solucion definitiva del Hardware con la inestabilidad del driver de parte de ubuntu cuando ellos la tengan.
[/SIZE] 
[SIZE=2]Como informacion extra puedes tambien revisar la siguiente documentacion oficial de ubuntu en respecto a la aceleracion grafica:
[http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica]("http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica")[/SIZE]

[SIZE=2]**_Nota:_** Antes de modificar cualquier cosa en  "blacklist.conf" favor realiza un Backup en caso de tener problema para  que asi puedas volver a la configuracion original.

Saludos cordiales[/SIZE],

---

### Post by teko83 on 2010-12-24
Pucha, vi lo de blacklist y no tengo mi tarjeta en el listado, reinstalé compiz y nada... no se que hacer realmente, porque intento modificar las apariencias y lo hace, peor muevo el mouse y vuelve a estar sin efectos y más encima se me pega la preferencia de apariencia :confused:

---

### Post by moreback on 2010-12-25
Por favor revisa este link: [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Lo que dice es que pruebes primero corriendo en un terminal:

```
 SKIP_CHECKS=yes compiz --replace
```

Si te funciona entonces tendrías que escribir SKIP_CHECKS=yes en el archivo ~/.config/compiz/compiz-manager

Saludos.

---

### Post by teko83 on 2010-12-26
moreback, seguí tu instrucción, y me funcionaron algunas funcionalidades del compiz. Sin embargo no logré hacer funcionar a todas y además no entendí que archivo modificar, ya que el que me especificas no aparece 
Saludos

---

### Post by moreback on 2010-12-26
Si no aparece que el archivo simplemente tienes que crearlo.

---

### Post by RafaelG on 2010-12-28
Teko83,

Tienes que tener en cuenta que la solucion es para sacar tu tarjeta de video de la blacklist pero lo mas probable es que puedas presentar alguna inestabilidad con algunos efectos de Compiz, trata de tener en cuenta eso!

Saludos,

---

### Post by teko83 on 2010-12-28
RafaelG
Probaré de nuevo con el tema del blacklist y te comento como me fue
Saludos

---

### Post by teko83 on 2011-01-01
RafaelG, busqué la tarjeta en el blacklist, y aun no logro encontrarla, te adjunto mi archivo para ver si me puedes ayudar

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

Saludos y feliz año 2011

---

### Post by moreback on 2011-01-01
teko83, ese el blacklist del kernel, nada tiene que ver con compiz. Por favor, guíate según el link que te dí.

Saludos.

---

### Post by RafaelG on 2011-01-02
Teko83,

Efectivamente lo que indica moreback es correcto pero con la indicaciones antes mencionadas por moreback deberias solucionar el problema de la tarjeta de video

			 		   		 		 		> Por favor revisa este link: [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Lo que dice es que pruebes primero corriendo en un terminal:

 	Code:
 	 SKIP_CHECKS=yes compiz --replace 
Si te funciona entonces tendrías que escribir SKIP_CHECKS=yes en el archivo ~/.config/compiz/compiz-manager

---


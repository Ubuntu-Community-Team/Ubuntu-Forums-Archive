---
title: "Sin sonido en Karmic Koala"
date: 2009-10-30
forum: Software
---

### Post by Vero1 on 2009-10-30
Saludos a todos,

Una vez mas me veo en la obligación de pedirles ayuda.

Acabo de hacer upgrade a Karmic Koala. Despues de hacer update, empecé a probar cosas, como supongo hace todo el mundo. La cuestión es que tengo un problema serio, entre otras cositas.

El mayor problema es que no logro tener sonido. Estuve googleando toda la tarde, pero no lo logro.
Tengo instalado: Alsa, pulseaudio,MPlayer, SMPlayer, VLC, pero con ninguno puedo escuchar unos videos que tengo, ni en YouTube y que con la versión anterior no tenía ningun problema.

Cuando voy a Sistema-Preferencias-Sonido, en Hardware no figura nada, en Entrada no hay dispositivos, en Salida, Salida boba-Aplicaciones, ninguna.

Desde consola lspci, me sale
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
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
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

disculpen la longitud.

La verdad es que me siento decepcionada con ésto y agradecería una ayuda para solucionar el problema.

Muchas gracias y saludos

---

### Post by BlackHero on 2009-10-30
hola vero como estas, me podrias pasar los logs del sistema, y decime que hard tenes, probaste reinstalando alsa? 

proba tipeando este comando en consola

cat /proc/asound/modules
 

y decime que te da el mensaje de salida

saludos

---

### Post by hunterofhell on 2009-10-30
Saludos, yo tengo el mismo problema con el koala, con la versión anterior 9.04 funcionaba normal el sonido pero ahora no me funciona para naa, por apurado no me fije y me baje el cd para actualizar :( pensando q era el instalador, en vez de instalar desde 0 tuve q actualizar a la versión 9.10. Por favor si hay una solución para arreglar el sonido o si es q mejor me bajo el instalador del 9.10 para instalar desde 0.
Esto me bota el lspci:
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0b.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

y del cat /proc/asound/modules:
0 snd_cmipci
1 saa7134_alsa

Espero su ayuda gracias

---

### Post by guillermolisi on 2009-10-30
> **BlackHero said:**
> hola vero como estas, me podrias pasar los logs del sistema, y decime que hard tenes, probaste reinstalando alsa? 

proba tipeando este comando en consola

cat /proc/asound/modeules
 

y decime que te da el mensaje de salida

saludos
La linea de comando correcta es ```
cat /proc/asound/modules
```

Por favor, revisar lo que escribis cuando se tratan de lineas de comando.

---

### Post by jandry on 2009-10-31
Hola amigos del foro, actualice y tengo el mismo problema, tipee el comando que pasaron y sale 0 snd_hda_intel si alguien tiene una punta que avise. Abrazo ubuntero
Alejandro

---

### Post by Zevangelion on 2009-10-31
Hey yo tambien tengo el mismo problema ;____;  y cuando tipee el comando en la consola salio esto:

 0 snd_hda_intel


Acabo de instalarlo hoy D: ¿Hay alguna solucion ;__;?

---

### Post by Vero1 on 2009-10-31
Hola todos,

Gracias por las respuestas.
Justo iba a escribirles para decirles que se ha solucionado el problema del sonido, no sé cómo en realidad, pero les cuento lo que hice.

Pero antes les comento que por curiosidad acabo de probar el comando cat /proc/asound/modules y me contesta
0 snd_hda_intel, pero tengo sonido.

Bueno, a lo que interesa. 

Además del problema del sonido, me llamaba la atención que en el Grub figuraba  - versión 9.10 pero haciendo referencia a Jaunty, probé entrar en Modo Recovery. Elegí entre las opciones: Update grub bootloader para ver si cambiaba, cosa que no pasó pero despues que terminó la pantalla del Recovery me mandó a tty para que me loguee. Lo hice pero no pasaba a GDM, por lo tanto le indiqué sudo gdm start. Me pidió usuario y contraseña y despues de eso ya entré en el escritorio Gnome y para mi sorpresa ya tenía sonido.

Comento todo ésto por si a alguien le sirve.

Gracias de nuevo por su atención y saludos. ;)

---

### Post by autusgo on 2009-10-31
A ver si es lo mismo que me pasa a mí. Pasé a Karmic y desde entonces no tengo sonido; en realidad me di cuenta que con algunas applicaciones tengo sonido **muy** bajito.

Cuando prendo la máquina me aparece un cartel que dice que se detectó un cambio en el hardware; algo así como que no detecta la placa de sonido que tenía antes y me pregunta si la quiero borrar, a lo que siempre respondo que no.

Fui a System Settings -> Multimedia y en la parte de Audio Output veo 4 cosas:

HDA NVidia (ALC883 Analog)
HDA NVidia (ALC88 Digital)
[COLOR=Gray]HDA NVIdia, AL889 Digital (IEC958 (S/PDIF) Digital Audio Output[/COLOR]
PulseAudio

En ese orden. Estoy casi seguro que yo antes usaba la tercera (que ahora está en gris).

Alguien tiene alguna idea?
Ahh probé con el comando que le pasaron a Vero1 y me sale esto:
 0 snd_hda_intel
 1 saa7134_alsa

Gracias!

---

### Post by Zevangelion on 2009-10-31
> **Vero1 said:**
> Hola todos,

Gracias por las respuestas.
Justo iba a escribirles para decirles que se ha solucionado el problema del sonido, no sé cómo en realidad, pero les cuento lo que hice.

Pero antes les comento que por curiosidad acabo de probar el comando cat /proc/asound/modules y me contesta
0 snd_hda_intel, pero tengo sonido.

Bueno, a lo que interesa. 

Además del problema del sonido, me llamaba la atención que en el Grub figuraba  - versión 9.10 pero haciendo referencia a Jaunty, probé entrar en Modo Recovery. Elegí entre las opciones: Update grub bootloader para ver si cambiaba, cosa que no pasó pero despues que terminó la pantalla del Recovery me mandó a tty para que me loguee. Lo hice pero no pasaba a GDM, por lo tanto le indiqué sudo gdm start. Me pidió usuario y contraseña y despues de eso ya entré en el escritorio Gnome y para mi sorpresa ya tenía sonido.

Comento todo ésto por si a alguien le sirve.

Gracias de nuevo por su atención y saludos. ;)

Lo hice así,pero no funciono D_: Me vuelvo loco sin sonido x___x

---

### Post by alfplayer on 2009-11-01
Vero probablemente estaba usando un kernel viejo por no haberse actualizado bien grub.

autusgo la que está en gris es la salida digital. Tiene que estar seleccionada la que se usa, lo común es usar salidas analógicas.
Si las barras de volumen están al máximo puede haber problemas con el driver.

---

### Post by Zevangelion on 2009-11-01
Ya lo solucioné xO.Estuve buscando por el foro de Ubuntu in inglich y encontré esta página:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


Resulta que hice lo que dice ahi,instale ''Pulse Audio Device Chooser'' tipee este comando en la consola:

alsamixer -Dhw

y tenia todos las barras de volumen apagadas o_OU las subi y eureka ;D

---

### Post by andoni on 2009-11-09
Pues yo lo que hice fue reinstalar todos los paquetes ALSA de mi sistema, et voilà! ya tenía sonido de nuevo en Ubuntu.

EDIT: Acabo de comprobar que, al hacer un reboot, vuelvo a quedarme sin sonido...

Saludos.

---

### Post by bboywilmer on 2009-11-25
hola una solución que me cirvio fue esta:
[http://bitelia.com/2009/11/como-arreglar-problemas-de-sonido-en-ubuntu-910#comment-116797](http://bitelia.com/2009/11/como-arreglar-problemas-de-sonido-en-ubuntu-910#comment-116797)
espero les funcione como a mi.
EXITOS

---


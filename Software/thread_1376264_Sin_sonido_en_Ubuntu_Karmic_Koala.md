---
title: "Sin sonido en Ubuntu Karmic Koala"
date: 2010-01-09
forum: Software
---

### Post by Miss Fenriz on 2010-01-09
En primer lugar aclaro que posteo este problema aqui pues parece ser mas bien de software que de hardware, pues Ubuntu me reconoce la tarjeta de sonido y en Windows XP funciona bien. Si el tema es para otro subforo ruego disculpar por ello.

Luego de instalar Ubuntu 9.10 Karmic Koala (instalacion fresca en disco duro nuevo, no actualizacion) me di cuenta que tenia un problema que no se habia dado en las anteriores versiones: el sistema no tiene sonido. Es decir, cuando conecto los parlantes o audifonos al pc y comienzo a reproducir una cancion o video no se escucha nada, aparte de un ligero ruido estatico. Cabe mencionar que instale los paquetes de los extras restrictivos asi que no es ese el problema. El indicador de la pantalla aparece al maximo de volumen, en el menu "sonido" todos los indicadores de altavoz estan al maximo y la tarjeta de sonido aparece listada y reconocida. Probe desinstalando y reinstalando Pulseaudio, pero no funciono.

Como ya dije, estoy usando Ubuntu 9.10 en un Intel Pentium Dual Core E2160 y la tarjeta de sonido es una via VT1708/A. No se me ocurre que otra informacion podria requerir...

Si alguien mas ha tenido este problema o sabe que puede estar ocurriendo, le pido que por favor me oriente para solucionarlo. De antemano gracias a todos.

---

### Post by moreback on 2010-01-09
Primero revisa en **Sistema -> Preferencias -> Selector de sistemas multimedia **y ve qué dispositivos estás usando para reproducción de audio. Yo en la pestaña de **Audio** tengo todo en **PulseAudio Sound Server**.

Si no te funciona, pega la salida del comando **lspci** para identificar con más detalle la tarjeta de sonido que tienes.

Saludos.

---

### Post by Miss Fenriz on 2010-01-10
> **moreback said:**
> Primero revisa en **Sistema -> Preferencias -> Selector de sistemas multimedia **y ve qué dispositivos estás usando para reproducción de audio. Yo en la pestaña de **Audio** tengo todo en **PulseAudio Sound Server**.


Me voy al menu, pero no tengo la opcion de "selector de sistemas multimedia". No se si sera por que tengo un usuario creado y no trabajo directamente con el root.

> **moreback said:**
> Si no te funciona, pega la salida del comando **lspci** para identificar con más detalle la tarjeta de sonido que tienes.

Aqui esta:

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
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

Muchas gracias por tu respuesta y poner atencion a mi problema.

---

### Post by moreback on 2010-01-10
> **Miss Fenriz said:**
> Me voy al menu, pero no tengo la opcion de "selector de sistemas multimedia". No se si sera por que tengo un usuario creado y no trabajo directamente con el root.

Si no aparece puedes ejecutarlo con Alt+F2 y luego escribir **gstreamer-properties**

Tu tarjeta sería **80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)** por lo que con esto ya podemos buscar información en los foros.

Saludos cordiales.

---

### Post by Miss Fenriz on 2010-01-10
> **moreback said:**
> Si no aparece puedes ejecutarlo con Alt+F2 y luego escribir **gstreamer-properties**

Saludos cordiales.

Ya lo hice, esta todo con Pulseaudio como default.

> **moreback said:**
> Tu tarjeta sería **80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)** por lo que con esto ya podemos buscar información en los foros.

Busque informacion en google y varios foros (parece ser comun que esa tarjeta tenga problemas con Karmic). He intentado varias soluciones pero nada funciona: reinstale alsa y pulseaudio, los desinstale, los reinstale desde synaptic, compile el codigo de alsa para reinstalarlo nuevamente y nada. Sigo sin audio y bajo la amenaza de no permitirme instalar Ubuntu nuevamente...

Igualmente agradezco mucho tu ayuda y tus respuestas :)

---

### Post by Carlos C on 2010-01-11
¿Es un notebook?

Te sugiero hacer una prueba. Mata el proceso de pulseaudio:
```
sudo killall pulseaudio
```
cargas alsa
```
sudo alsa force-reload
```
Luego verifica las opciones que te señala moreback y cambialas a alsa. Con "alsamixer" verifica que estés con volumen. Si te funciona es cosa de evitar que pulseaudio se cargue al iniciar la sesión, sino, volver atrás es tan simple como seleccionar pulseaudio y reiniciar.

Si eso no te funciona te sugiero que mires esta página:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)


Saludos.

---

### Post by Miss Fenriz on 2010-01-11
> **Carlos C said:**
> ¿Es un notebook?

No, es un desktop. Es un pc armado, asi que no se si en eso pueda radicar el problema... ya que yo habia instalado Karmic antes (en noviembre) y tuve el mismo problema de audio pero lo solucione reinstalando alsa y nada mas. Ahora como compre otro disco duro (ya que comparto equipo con mi hermano y me elimino las particiones) hice la instalacion fresca de Karmic y no he podido dar con la solucion al asunto del sonido.

> **Carlos C said:**
> 
Te sugiero hacer una prueba. Mata el proceso de pulseaudio:
```
sudo killall pulseaudio
```cargas alsa
```
sudo alsa force-reload
```

El primer comando funciono, pero al usar **sudo alsa force-reload** me dio el siguiente error:

```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/iskra/.gvfs
      Output information may be incomplete.
Terminating processes: 1614lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/iskra/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/iskra/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/iskra/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-via snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-via snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

```

> **Carlos C said:**
> 
Luego verifica las opciones que te señala moreback y cambialas a alsa. Con "alsamixer" verifica que estés con volumen. Si te funciona es cosa de evitar que pulseaudio se cargue al iniciar la sesión, sino, volver atrás es tan simple como seleccionar pulseaudio y reiniciar.

Si eso no te funciona te sugiero que mires esta página:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Saludos.

Estuve leyendo la pagina y aplicando los pasos. Luego de eso probe nuevamente y sigo sin sonido en mis parlantes, pero al conectar los audifonos tengo un ligero sonido muy bajo y opacado por un rudio estatico. Probablemente me falte configurar algo mas, he probado dejando pulseaudio o alsa como default pero el asunto persiste. En uno de los pasos de aquella pagina daba la opcion de pegar el log en pastebin y asi lo hice, aqui esta el link: [http://pastebin.ca/1747667](http://pastebin.ca/1747667)

En verdad que estoy agradecida de la ayuda y las respuestas que he recibido. Saludos.

---

### Post by kamus on 2010-01-12
Al ejecutar alsamixer (en una terminal) deberias ver algo así:

[IMAGEN ALSAMIXER]("http://www.korporation.cl/blog/wp-content/uploads/2009/07/alsamixer.jpg")

Sube los niveles del Master y PCM (con las flechas del teclado arriba y abajo los manejas), luego presiona escape (ESC) e intenta reproducir algún archivo/mp3/wav/etc.

Salu2

---

### Post by CdK1 on 2010-01-14
Antes que todo hubiese empezado con un alsaconf, luego alsamixer y revisar los log al tratar de escuchar música...

---

### Post by Miss Fenriz on 2010-01-26
Al final pedi que me revisaran la tarjeta de sonido, la "apretaron" un poco y luego reinstale el alsa, el pulseaudio y al seleccionar este ultimo funciono bien. Muchas gracias a todos por su ayuda!

---

### Post by Waln on 2010-01-28
Hola.
Finalmente tengo sonido en Kamic64 con una VT1708/A.
Me funciono con selector de sistemas de multimedia debe estar en pulseaudio sound server, y NO debe tener instalado el linux-backports-modules-alsa (cada vez que lo instale, perdi el sonido).
Espero que tengan igual de suerte.
Saludos.-

---


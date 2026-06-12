---
title: "Problem with QjackCtl and line6usb drivers"
date: 2013-05-18
forum: Ubuntu Studio
---

### Post by Zilveztre on 2013-05-18
Ok, as the title says... I can't make Qjackctl start on my ubuntu studio 12.10. I recently installed it from scratch because I changed the HDD of my notebook.

On 3 days I managed to get working World of Warcraft under wine, League of Legends under wine and almost every programming/developing platform I need for my studies and the languages/extensions I need to use... the only thing that's left is to make work my POD Studio UX2 and I can finally say goodbye to Winbugs. Any help would be greately appreciated!

Here's what I get when I try to start Qjackctl:
>   [COLOR=#999999]10:07:16.231 Patchbay desactivada.[/COLOR]
 [COLOR=#999999]10:07:16.364 Reiniciar estadísticas.[/COLOR]
 [COLOR=#cccc99]10:07:16.372 Cambios en las conexiones ALSA.[/COLOR]
 [COLOR=#999999]10:07:16.392 D-BUS: Disponible (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]10:07:16.635 D-BUS: El servidor JACK no puede iniciarse. Disculpa[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]10:07:16.685 Cambió el gráfico de conexiones ALSA.[/COLOR]
 Sat May 18 10:07:16 2013: Starting jack server...
 Sat May 18 10:07:16 2013: JACK server starting in realtime mode with priority 10
 Sat May 18 10:07:16 2013: control device hw:2
 Sat May 18 10:07:16 2013: control device hw:2
 Sat May 18 10:07:16 2013: [1m[31mERROR: Failed to acquire device name : Audio2 error : Cannot allocate memory[0m
 Sat May 18 10:07:16 2013: [1m[31mERROR: Audio device hw:2 cannot be acquired...[0m
 Sat May 18 10:07:16 2013: [1m[31mERROR: Cannot initialize driver[0m
 Sat May 18 10:07:16 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sat May 18 10:07:16 2013: [1m[31mERROR: Failed to open server[0m
 Sat May 18 10:07:17 2013: Saving settings to "/home/german/.config/jack/conf.xml" ...
 [COLOR=#ff0000]10:07:18.893 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server request channel
 jack server is not running or cannot be started


Sometimes it starts flawlessly but whenever I touch the volume control on my UX2 or on the computer it stops and gives me an error msg... 

Here's what I get on arecord -l:
> german@Asd:~$ arecord -l
**** Lista de CAPTURE dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC269VB Analog [ALC269VB Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: PODStudioUX2 [POD Studio UX2], dispositivo 0: POD Studio UX2 [POD Studio UX2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


And here's what I get on aplay -l:
> german@Asd:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC269VB Analog [ALC269VB Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Generic [HD-Audio Generic], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: PODStudioUX2 [POD Studio UX2], dispositivo 0: POD Studio UX2 [POD Studio UX2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


So... the hardware is detected... but somehow jack can't communicate with it so well... :?

Any help?

Thanks!


Btw: My computer is an Asus K52dr. 6Gb RAM Ddr3. AMD Phenom triple core. And i'm running "3.5.0-28-lowlatency" of Ubuntu Studio 12.10 completely up to date.

[COLOR=#ff0000]Edit: When the Jack server starts succesfully and I try to route something to the UX2 now I get this:
> [/COLOR][COLOR=#ff0000]  [/COLOR]Sat May 18 10:29:35 2013: [1m[31mERROR: ALSA: poll time out, polled for 8706070 usecs[0m
 Sat May 18 10:29:35 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
 [COLOR=#66cc99]10:29:51.928 Cambió el gráfico de conexiones ALSA.[/COLOR]
 Sat May 18 10:29:51 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:29:51 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:29:51 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:30:39 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:30:39 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:30:39 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:31:39 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:31:39 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:31:39 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:31:44 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:31:44 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:31:44 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:32:08 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:32:08 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:32:08 2013: [1m[31mERROR: Cannot create new client[0m
 [COLOR=#66cc99]10:32:12.864 Cambió el gráfico de conexiones ALSA.[/COLOR]
 Sat May 18 10:32:13 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:32:13 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:32:13 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:32:37 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:32:37 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:32:37 2013: [1m[31mERROR: Cannot create new client[0m
 Sat May 18 10:32:42 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:32:42 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:32:42 2013: [1m[31mERROR: Cannot create new client[0m
 (qjackctl.real:2541): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2541): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Sat May 18 10:38:19 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Sat May 18 10:38:19 2013: [1m[31mERROR: Driver is not running[0m
 Sat May 18 10:38:19 2013: [1m[31mERROR: Cannot create new client[0m
 (qjackctl.real:2541): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2541): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]And when I try to open Rakarrack a message window appears that says that no jack server is detected :?[/COLOR]

---

### Post by zequence on 2013-05-20
Are you using the same device for pulseaudio?

---

### Post by Zilveztre on 2013-05-20
To be honest, I've no idea... I'm pretty new in this area! How do I check that out?

---

### Post by zequence on 2013-05-20
Check out [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro).

pulseaudio is the default desktop audio server used on Ubuntu distributions. jack is a pro audio server, that on Ubuntu Studio you start separately. 

Currently, there is a bug in pulseaudio stopping you from starting jack if you are using the card with pulseaudio for something. Make sure your card is not used for anything else when starting jack.

---

### Post by Zilveztre on 2013-05-20
Still... I don't know how to check that :S

---

### Post by zequence on 2013-05-20
The question remains, are you using the same device for desktop audio as you are for jack? pulseaudio is the desktop audio server that you can control from the volume applet, while jack is the pro audio server that you start with qjackctl.

---

### Post by Zilveztre on 2013-05-20
Nop, for my desktop audio I use my integrated sound card... as for jack I intend to use my usb POD Studio UX2.

---

### Post by zequence on 2013-05-21
If you are able to start jack with your usb device, then it works. I was getting the impression that this was the case.

If it stops working because of you changing the volume on it, I would say that it is some kind of a bug in ALSA. If this is the case, then it would be good to report a bug. Get a launchpad account at [http://launchpad.net](http://launchpad.net), then in the terminal, do:

```
ubuntu-bug alsa-base
```

Also, take the opportunity to join the ubuntustudio user team in launchpad :) [https://launchpad.net/~ubuntustudio](https://launchpad.net/~ubuntustudio).

---

### Post by Zilveztre on 2013-05-21
Actually, that's the thing... I can't start jack server now with my usb. Miraculously I could that time but now I can't :?

---

### Post by Zilveztre on 2013-05-23
Well, I'm here again... I uninstalled Pulseaudio and reinstalled alsa to try that out... but still, no luck on getting jack to work. When I was with alsa and pulseaudio uninstalled y started the server selecting my POD Studio UX2 and I heared sound on it. But now I installed alsa again (So I can have my desktop sound) and no luck again. What am I missing? -.-

---

### Post by zequence on 2013-05-23
Pulseaudio may only be a problem if you're starting jack on the same card that pulseaudio is using, and only in certain situations. With Ubuntu Studio 13.04, there is more or less no problems with that. So, uninstalling pulseaudio will not help you.

I'm more inclined to believing that what you need to to do is set good options in your jack settings.

---

### Post by Zilveztre on 2013-05-23
Here's two pictures of my configurations on jack:

[IMG]http://imageshack.us/a/img833/1637/asdasdasd1.png[/IMG]

[IMG]http://imageshack.us/a/img18/7996/asdasd2p.png[/IMG]


You tell me if I'm doing something wrong. Thanks!

---

### Post by zequence on 2013-05-23
Looks fine to me. I don't know your device, so I don't know how many channels it supports. You could try, for the sake of troubleshooting, to start it in non-duplex mode, meaning only output or input. But this is mostly only useful with devices that have more than 2 I/O.

I read somewhere just now that this device is supposed to be supported. But, it is kind of hard finding any good information about it. Can't seem to find anything on alsa's home page. You could try posting to the linux audio user mail list [http://lists.linuxaudio.org/listinfo/linux-audio-user](http://lists.linuxaudio.org/listinfo/linux-audio-user), or check out [http://www.linuxmusicians.com/](http://www.linuxmusicians.com/).

---

### Post by Zilveztre on 2013-05-23
Ok, I'll try that... and yes, this usb interface have a lot of good comments about how it works on linux (almost any distro). That's what brings me down, I want to use ubuntu and leave windows behind. Making my UX2 work would complete all the things I use on my pc. 

Hope I can make it work, thank you for your time!

---


---
title: "Edirol UA-25 issue"
date: 2012-09-09
forum: Ubuntu Studio
---

### Post by batmacumba on 2012-09-09
hello, i have a Dell xps 15 with ubuntu 12.04 installed. recently, i  purchased a edirol ua-25 usb audio interface and even though it is  recognized by the computer and seems to work with jack, i can't get any  input sound of it in ardour.
i have searched many forums looking for an answer or a simple way to  fresh-install the audio interface, but i am really new to linux so i  don't understand the most of the hypothetical solutions.
i tried configuring just like the ubuntu studio webpage told me, with jack and ardour but still i get no sound- also, in the jack connections it appears not just system and ardour, it shows pulseaudio JACK sink/source too.
i think i could get input sound before, and i THINK pulseaudo wasn't in the jack connections, but i am just speculating

please, any guidance would be greatly thanked

José

---

### Post by jejeman on 2012-09-09
Give us output from
```
aplay -l
```

---

### Post by batmacumba on 2012-09-09
> **jejeman said:**
> Give us output from
```
aplay -l
```
ok, this is the output: 

```
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: PCH [HDA Intel PCH], dispositivo 0: ALC665 Analog [ALC665 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 1: ALC665 Digital [ALC665 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: UA25 [UA-25], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```i tried this before, and i see that the device is recognized, so i think it's not a hardware issue, i think is some configuration issue. but then again, i am a total noob on this. sorry, the output is in spanish

---

### Post by jejeman on 2012-09-09
Okay, card is recognized. Try to select it in qjackctl as interface. It should be card 1.

---

### Post by batmacumba on 2012-09-09
yes, it is set as an interface. it shows UA-25 as 1 and USB audio as 1,0. it is set to 1.

---

### Post by batmacumba on 2012-09-09
damn, now i can't even start jack. it fails to start and the message window tells me this:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]18:05:08.161 Patchbay desactivada.[/COLOR]
 [COLOR=#999999]18:05:08.162 Reiniciar estadísticas.[/COLOR]
 [COLOR=#cccc99]18:05:08.173 Cambios en las conexiones ALSA.[/COLOR]
 [COLOR=#999999]18:05:08.194 D-BUS: Disponible (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]18:05:08.205 Cambió el gráfico de conexiones ALSA.[/COLOR]
 [COLOR=#ff0000]18:05:20.403 D-BUS: El servidor JACK no puede iniciarse. Disculpa[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started
 Sun Sep  9 18:05:20 2012: Starting jack server...
 Sun Sep  9 18:05:20 2012: JACK server starting in realtime mode with priority 10
 Sun Sep  9 18:05:20 2012: control device hw:1
 Sun Sep  9 18:05:20 2012: control device hw:1
 Sun Sep  9 18:05:20 2012: [1m[31mERROR: Failed to acquire device name : Audio1 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
 [0m
 Sun Sep  9 18:05:20 2012: [1m[31mERROR: Audio device hw:1 cannot be acquired...[0m
 Sun Sep  9 18:05:20 2012: [1m[31mERROR: Cannot initialize driver[0m
 Sun Sep  9 18:05:20 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Sun Sep  9 18:05:20 2012: [1m[31mERROR: Failed to open server[0m
 Sun Sep  9 18:05:22 2012: Saving settings to "/home/julio/.config/jack/conf.xml" ...
 [COLOR=#ff0000]18:05:25.829 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
 Cannot connect to server socket err = No existe el archivo o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started
```

---

### Post by batmacumba on 2012-09-09
help, anybody?

---

### Post by sgx on 2012-09-09
Hi, the usb device order as detected by qjackctl, can change
between boots. Configure qjackctl to not start jackd, in the
Setup page, Misc tab. You then just open the Input Device >
setup on the right side of the setup page,
and choose the device you want, and the start qjackctl.

Keyboard and guitar players often use different interfaces,
so it is handy to use this option.

The Periods/Buffer setting, should be 3 for usb and firewire devices.
The output of aconnect -i   and arecord -l
should mention the Edirol, and click Input Device >  widget
(  >  ) to see and select from the list of sound devices detected.

Cheers

---


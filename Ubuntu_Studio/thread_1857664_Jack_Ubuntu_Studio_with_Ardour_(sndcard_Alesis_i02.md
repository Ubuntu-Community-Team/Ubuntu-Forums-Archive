---
title: "Jack Ubuntu Studio with Ardour (sndcard Alesis i02): can't connect to server socket"
date: 2011-10-10
forum: Ubuntu Studio
---

### Post by reviratempos on 2011-10-10
[COLOR=#999999]Good morning,[/COLOR]
[COLOR=#999999]I have been trying to begin recording. I succeeded   in recording one piano track, but made a change regarding latency, and   since then have been unable to get jack  to work. Therefore I have come here for the first time to to ask for  help. Can anyone direct me as  to how to proceed?  The following the log  information over the last few  weeks.[/COLOR]


Any help is Greatly Appreciated. Thanks.

[COLOR=#999999]
[/COLOR]
[COLOR=#999999]14:05:41.600 Patchbay desactivada.[/COLOR]
 [COLOR=#999999]14:05:41.614 Reiniciar estadísticas.[/COLOR]
 [COLOR=#cccc99]14:05:41.696 Cambios en las conexiones ALSA.[/COLOR]
 Cannot connect to server socket err = No existe el fichero o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]14:05:41.707 Cambió el gráfico de conexiones ALSA.[/COLOR]
 [COLOR=#99cc66]14:05:41.900 Escaneo del patchbay ALSA activo...[/COLOR]
 [COLOR=#999999]14:05:47.946 JACK está iniciándose...[/COLOR]
 [COLOR=#990099]14:05:47.947 /usr/bin/jackd -P1 -u -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1 -i1[/COLOR]
 Cannot connect to server socket err = No existe el fichero o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#999999]14:05:47.980 JACK se inició con PID=2452.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 1
 control device hw:1
 control device hw:1
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1|hw:1|1024|2|44100|1|0|nomon|swmeter|-|32bit
 control device hw:1
 Using ALSA driver USB-Audio running on card 1 - Alesis io|2 at usb-0000:00:1d.0-1.2, full speed
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: cannot set channel count to 1 for capture
 ALSA: cannot configure capture channel
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]14:05:48.545 JACK ha sido detenido con estado 255.[/COLOR]
 [COLOR=#ff0000]14:05:50.109 No puede conectarse al servidor JACK   como cliente. - La operación global falló. - No puede conectarse al   servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]
 Cannot connect to server socket err = No existe el fichero o el directorio
 Cannot connect to server socket
 jack server is not running or cannot be started

---

### Post by sgx on 2011-10-11
Hi, these links have pics and info to manage connections.

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

On the middle right of the qjackctl setup panel are

Input device  >
Output device >

click the  > widgets to find your alesis. It may have a different
hw:  number if different usb devices are added or removed.

Choose  3  for the periods/buffer setting in qjackctl.

Looks like an excellent interface!

Cheers

---


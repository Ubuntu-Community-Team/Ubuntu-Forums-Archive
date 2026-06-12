---
title: "Qjack control don't sound"
date: 2012-09-01
forum: Ubuntu Studio
---

### Post by rusoRBP on 2012-09-01
Hi, 

My problem is the jack don't sound,but the server work aparently.
I've read a lot of tutorials about jack configurations, but I don't get solve it.

In connections, audio tab, writable clients/ input port, no appear 'systen' (playback), maybe this is the problem.

Show this picture for more imformation:
[http://img269.imageshack.us/img269/3803/problemadz.png](http://img269.imageshack.us/img269/3803/problemadz.png)

Thanks!!

---

### Post by jejeman on 2012-09-01
>  In connections, audio tab, writable clients/ input port, no appear 'systen' (playback), maybe this is the problem.Yes that is problem. If you don't have playback ports you can't have output sound to speakers.

Did you set jack to work in duplex mode?

give us output from
```
aplay -l
```

---

### Post by rusoRBP on 2012-09-01
yes, I set jack to work in duplex mode. 
[http://img802.imageshack.us/img802/8788/configr.png](http://img802.imageshack.us/img802/8788/configr.png)

output from aplay -l

[I]ruso@ubuntustudio:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
ruso@ubuntustudio:~$ [/I]

---

### Post by sgx on 2012-09-01
Hi, look at links 4 first, and then 8 at this wiki:

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

to see jackd, and qjackctl setup. On the qjackctl Setup page
Input Device >
Output Device >

click the > to see sound hardware you have, select intel in both,
and restart qjackctl. Hold the keyboard keys down with some object,
so you can hear when connections are a success. You must connect
zynaddsubfx in both the alsa, and audio tabs.

The wiki link 8 has screenshots of zynaddsubfx in qjackctl. Don't start with rosegarden, until your sound is working.  
Also try using the phasex synth, as it autoconnects in the audio tab,
and you connect it in the alsa tab, which is your midi keyboard connector.

(the Midi tab is for a2jmidid users)
Cheers

---

### Post by rusoRBP on 2012-09-02
SGX, thanks for the info

Now I have another problem, if I don't start rosegarden before qjackctl, the server doesn't work. Why?

This is message window:

 p, li { white-space: pre-wrap; }  *[COLOR=#999999]11:30:04.699 Patchbay desactivada.[/COLOR]*
 *[COLOR=#999999]11:30:04.817 Reiniciar estadísticas.[/COLOR]*
 *[COLOR=#cccc99]11:30:04.864 Cambios en las conexiones ALSA.[/COLOR]*
 *[COLOR=#999999]11:30:04.926 JACK está iniciándose...[/COLOR]*
 *[COLOR=#990099]11:30:04.927 /usr/bin/jackd -S -dalsa -r48000 -p512 -n2 -D -Chw:0,1 -Phw:0,4[/COLOR]*
 *Cannot connect to server socket err = ConexiÃ³n rehusada*
 *Cannot connect to server socket*
 *jack server is not running or cannot be started*
 *Cannot connect to server socket err = ConexiÃ³n rehusada*
 *Cannot connect to server socket*
 *jack server is not running or cannot be started*
 *no message buffer overruns*
 *no message buffer overruns*
 *jackdmp 1.9.7*
 *Copyright 2001-2005 Paul Davis and others.*
 *Copyright 2004-2010 Grame.*
 *jackdmp comes with ABSOLUTELY NO WARRANTY*
 *This is free software, and you are welcome to redistribute it*
 *under certain conditions; see the file COPYING for details*
 *JACK server starting in realtime mode with priority 10*
 *control device hw:0*
 *control device hw:0*
 *audio_reservation_init*
 *Acquire audio card Audio0*
 *creating alsa driver ... hw:0,4|hw:0,1|512|2|48000|0|0|nomon|swmeter|-|32bit*
 *control device hw:0*
 *Using ALSA driver ICH4 running on card 0 - Intel ICH5 with ALC850 at irq 17*
 *configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods*
 *ALSA: final selected sample format for capture: 16bit little-endian*
 *ALSA: use 2 periods for capture*
 *ALSA: final selected sample format for playback: 16bit little-endian*
 *ALSA: use 2 periods for playback*
 *[COLOR=#999999]11:30:05.664 JACK se inició con PID=2077.[/COLOR]*
 *[COLOR=#ff0000]11:30:12.755 No puede conectarse al servidor JACK como cliente. - La operación global falló. - Error de comunicación con el servidor. Por favor revise la ventana de mensajes para mas información.[/COLOR]*
 *JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out*
 *Driver is not running*
 *JackSocketClientChannel read fail*
 *Cannot create new client*
 *Cannot open qjackctl client*
 *[COLOR=#999999]11:30:18.113 JACK está deteniéndose...[/COLOR]*
 *jack main caught signal 15*
 *[COLOR=#cccc99]11:30:40.075 Cambios en las conexiones ALSA.[/COLOR]*
 *[COLOR=#66cc99]11:30:40.093 Cambió el gráfico de conexiones ALSA.[/COLOR]*

---


---
title: "problem with xruns"
date: 2012-04-19
forum: Ubuntu Studio
---

### Post by rusoRBP on 2012-04-19
Hello all,

I'm new in ubuntu and I have problems with jackclt.
It don't work because appear xruns.

This is the message of jack control:

 p, li { white-space: pre-wrap; }  *[COLOR=#999999]10:12:17.914 JACK se inició con PID=5879.[/COLOR]*
 *no message buffer overruns*
 *JACK compiled with System V SHM support.*
 *loading driver ..*
 *apparent rate = 48000*
 *creating alsa driver ... hw:ICH5|hw:ICH5|512|2|48000|0|0|nomon|swmeter|-|32bit*
 *configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods*
 *ALSA: final selected sample format for capture: 16bit little-endian*
 *ALSA: use 2 periods for capture*
 *ALSA: final selected sample format for playback: 32bit integer little-endian*
 *ALSA: use 2 periods for playback*
 *[COLOR=#66cc99]10:12:18.290 Cambió el gráfico de conexiones ALSA.[/COLOR]*
 *[COLOR=#999933]10:12:19.945 Configuración del servidor salvada en "/home/ruso/.jackdrc".[/COLOR]*
 *[COLOR=#999999]10:12:19.947 Reiniciar estadísticas.[/COLOR]*
 *[COLOR=#999999]10:12:20.034 Cliente activado.[/COLOR]*
 *[COLOR=#999999]10:12:20.035 Script de post - inicio...[/COLOR]*
  *[COLOR=#cc66cc]10:12:20.114 XRUN callback (1).[/COLOR]*
 *[COLOR=#cc99cc]10:12:20.453 XRUN callback (18 omitidos).[/COLOR]*
 *[COLOR=#cc99cc]10:12:22.456 XRUN callback (93 omitidos).[/COLOR]*
 *[COLOR=#CC99CC]10:12:24.459 XRUN callback (93 omitidos).[/COLOR]*


this is the info of my system:
[http://paste.ubuntu.com/936579/](http://paste.ubuntu.com/936579/)


thanks for your help


cheers!

---

### Post by jejeman on 2012-04-19
What is your cpu?

---

### Post by rusoRBP on 2012-04-21
It's a Pentium 4,  3.00GHz

---

### Post by Sylos on 2012-04-21
You could try reducing the frames/period value down to 256 and see if that helps. 

Cheers

---

### Post by sgx on 2012-04-21
Hi, if the xruns are inaudible, it's no big deal.

If you post your .jackdrc textfile, it may hold a clue. It is written
to /home/you each time you change settings and restart qjackctl. (It is also a command line that you can use to start jackd, starting qjackctl
secondly.

yours will be different, mine has

jackd -P89 -t1000 -dalsa -r44100 -p256 -n2 -D -Chw:0,0 -Phw:0,0

-P89 gives maximum priority to jackd. For some, 70 is fine.

-p256 -n2  Raising these values adds latency, but may reduce xruns, try

-p512, or -p1024

or you could bump -n2 up to -n3 or n4, while at -p256. Either way.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 at the wiki, have screenshots and details that will help.
Cheers

---

### Post by rusoRBP on 2012-04-22
the  .jackdrc textfile:
/usr/bin/jackd -m -dalsa -dhw:0 -r44100 -p256 -n2 -S -Xseq

I changed the frame/period to 512 and 1024. I get to reduce the xruns, but don't delete.

but the real problem happen after 5 seconds:
jackd watchdog: timeout - killing jackd

and the jackclt freezes and i have to kill the jack to exit it.
does this happen because the xruns?

thanks

---

### Post by jejeman on 2012-04-22
Bigger frames = less xruns
You have reasonably fast cpu, so you should get okay performans from jack.
To many xruns can crash jack, especally if they appear in very short period, in fact many xruns are indicator that jack will crash.

Try to use only playback, and see what happens then.

---

### Post by rusoRBP on 2012-04-23
I've  used playback mode and happen the same things.
appear "jackd watchdog: timeout - killing jackd" and crash the jack
why?

but if I use for example the driver 'oss', in playback mode the jack is ok, and duplex mode appear xruns but the jack doesn't crash. the problem with this driver is i don't get sound from jack.
can the problem be the driver alsa?

Thanks for you reply.

---


---
title: "How to have an Alesis Multimix 4usb running in ubuntu 10.04?"
date: 2010-07-10
forum: Ubuntu Studio
---

### Post by maghoxfr on 2010-07-10
I have just bought the Alesis Multimix 4 USB. I had asked a few ubuntu users that owned this interface and they all told me it ran out of the box. Mine did not, it doesn't appear in jack and I couldn't record with qtractor. I think it might be some minor configuration issue or a missing package I might have not installed. It's class compliant in windows/mac, so for what I know it should run out the box in ubuntu, sadly for me, it did not.

What can I do to have it running?

I'll keep trying by myself, if I succeed I'll post it, but I could really, really use a friendly hand!

Thanks

---

### Post by Pablo_F on 2010-07-10
Just after connecting the usb port give the output of:

dmesg | tail -20
lsusb
cat /proc/asound/cards
cat /proc/asound/modules

Cheers! Pablo

---

### Post by maghoxfr on 2010-07-10
Hola Pablo, thanks for the reply, here's the output:


```
dmesg | tail -20
[   16.393506] [drm] Initialized drm 1.1.0 20060810
[   16.416558] CPU0 attaching NULL sched-domain.
[   16.416564] CPU1 attaching NULL sched-domain.
[   16.444068] CPU0 attaching sched-domain:
[   16.444071]  domain 0: span 0-1 level MC
[   16.444074]   groups: 0 1
[   16.444078] CPU1 attaching sched-domain:
[   16.444079]  domain 0: span 0-1 level MC
[   16.444081]   groups: 1 0
[   18.033357] CPU0 attaching NULL sched-domain.
[   18.033367] CPU1 attaching NULL sched-domain.
[   18.056080] CPU0 attaching sched-domain:
[   18.056085]  domain 0: span 0-1 level MC
[   18.056087]   groups: 0 1
[   18.056093] CPU1 attaching sched-domain:
[   18.056095]  domain 0: span 0-1 level MC
[   18.056096]   groups: 1 0
[   21.354725] NET: Registered protocol family 24
[   26.872368] eth0: no IPv6 routers present
[   77.004023] Clocksource tsc unstable (delta = -84908922 ns)
maghox@matias-desktop:~$ lsusb
Bus 002 Device 003: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 002 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
maghox@matias-desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdbef8000 irq 23
 1 [camera         ]: USB-Audio - USB camera
                      USB camera at usb-0000:00:02.0-3, full speed
 2 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-4, full s

```

---

### Post by Pablo_F on 2010-07-11
Hola!

Your usb card seems to be hw:2 or hw:default

Try these settings with the command line:

$jackd -dalsa -dhw:default -r48000 

Does jackd start? If not, what are the error messages?

Cheers! Pablo

---

### Post by maghoxfr on 2010-07-11
I just copied-pasted this into the terminal 

```
$jackd -dalsa -dhw:default -r48000 
``` 

but it replyed:

```
-dalsa: command not found
```

---

### Post by angelsguitar on 2010-07-11
> **maghoxfr said:**
> I just copied-pasted this into the terminal 

```
$jackd -dalsa -dhw:default -r48000 
``` 

but it replyed:

```
-dalsa: command not found
```

I believe there are a few typos on the command; it should be "-d alsa" (with a space in between). The same happens with the rest of the options. Try it like this:

> jackd -d alsa -d hw:default -r 48000

or this:

> jackd -d alsa -d hw:2 -r 48000

Here's the man page for jackd; it might be helpful:

[http://linux.die.net/man/1/jackd]("http://linux.die.net/man/1/jackd")

---

### Post by maghoxfr on 2010-07-11
The reply to " jackd -d alsa -d hw:default -r 48000 " is:

```
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
creating alsa driver ... hw:default|hw:default|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 2 - Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-4, full s
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

```

for "jackd -d alsa -d hw:2 -r 48000" is

```
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
creating alsa driver ... hw:2|hw:2|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 2 - Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-4, full s
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
```

But when I open Jackcontrol I don't see anything like an USB interface in there. The specs for this interface are 44.1kHz at 16-bit.

---

### Post by maghoxfr on 2010-07-11
I managed to solve it. It was kind of stupid, so I'm sorry. I went to preferences>sound>hardware and ticked the PCM2900 Audio Codec. It works now. One question remains, I had this user tweaked for audio, but now I downloaded the whole ubuntustudio packages under the recommendation of a Multimix 4 owner, I'll have to get rid of tons of packages I won't use, could I have avoided the step of installing the ubuntustudio packages?

Thank you very much for all the help and consideration.
PS: Suerte España en la final!

---

### Post by angelsguitar on 2010-07-11
Glad you worked it out:D!

No sabía que hablabas español...

---

### Post by maghoxfr on 2010-07-11
Si, soy de Uruguay. Y por casualidad, todos en este hilo hablamos español jaja! Muchas gracias por la ayuda.

---

### Post by angelsguitar on 2010-07-11
Bueno, ¡saludos desde Puerto Rico!

Por cierto, le acabo de escribir en otro hilo que usted inició sobre el Oxygen 61:

[http://ubuntuforums.org/showthread.php?t=1450151]("http://ubuntuforums.org/showthread.php?t=1450151")

Resulta que estaba considerando comprar uno de esos.  Bueno, pero no quiero "apoderarme" de este hilo y cambiar el tópico, si desea me responde allá...y me puede responder en español si prefiere ;)

Gracias.

---

### Post by Pablo_F on 2010-07-11
Hi Matías, don't worry too much about the programs you won't use. Uninstall them if you want to, but they are not consuming resources (CPU and RAM), only a few MB in your hard disk.

The "dalsa not found" message was because you copied my suggestion literally, "$" and all. You should not have copied the "$" which I wrote because I just meant "this is a user terminal". Spaces are not needed although they do not hurt either.

Anyway, according to what you comment, -r44100 was a better option, and in any case, use Jack Control to give the options and parameters for jackd, now that you have solved the problem.

Saludos! Pablo

---

### Post by maghoxfr on 2010-07-11
Thanks again Pablo, and first of all let me say Congratuluations on the World cup!

I'm such an idiot man,  pasting the "$" symbol...I'll consider that on future suggestions. I will just uninstall the programs that I know for sure I won't use, because as you say, it's just a few Mb to have them there.

Gracias!

---


---
title: "can't get any sound"
date: 2011-05-21
forum: Ubuntu Studio
---

### Post by chuning on 2011-05-21
hello - 

I'm trying to get to grips with Rosegarden, and failing, because I'm unable to get any sound out of it.  I've searched every where for how to get Jack Audio working, but cannot seem to get anywhere.  Can anyone tell me in idiot-proof steps what I should do?

Thanks

Chris

---

### Post by sgx on 2011-05-22
Details needed about your OS, kernel, soundcard, jackd and Rosegarden version, other apps that are working with sound.  etc

a basic command to start jackd

jackd -d alsa -r 44100

then start qjackctl, then Rosegarden. Start it from a terminal, so errors will be readable, kernel timer resolution is too low in
a lot of kernels.
Cheers

---

### Post by chuning on 2011-05-22
Thank you for your reply -

My sound card is apparently 

 HDA-Intel - HDA Intel
                      HDA Intel at 0xd6700000 irq 46

I'm using Ubuntu 10.10, Rosegarden 10.02

Other apps working with sound are Musescore, and Spotify and other internet things

---

### Post by chuning on 2011-05-22
I tried starting jackd from the terminal, and it came up with:

jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
`default' server already active
Failed to start server

---

### Post by Pablo_F on 2011-05-22
What is the output of:

lsof  |grep pcm

?

You have at least two audio servers competing for your audio card. Rosegarden needs jack and jack needs your audio card.  

Even if you get jack up and running and Rosegarden starts without a problem...

**Rosegarden does not make sounds by itself**. You need either an external synth (hardware or software) or a synth plugin (dssi).

Cheers, Pablo

---

### Post by chuning on 2011-05-22
The output of that is:

pulseaudi 4136      chris  mem       CHR      116,4                8052 /dev/snd/pcmC1D0p
pulseaudi 4136      chris   28u      CHR      116,4      0t0       8052 /dev/snd/pcmC1D0p
jackd     4276      chris  mem       CHR      116,8                9222 /dev/snd/pcmC0D0p
jackd     4276      chris  mem       CHR      116,9                9223 /dev/snd/pcmC0D0c
jackd     4276      chris    8u      CHR      116,8      0t0       9222 /dev/snd/pcmC0D0p
jackd     4276      chris    9u      CHR      116,9      0t0       9223 /dev/snd/pcmC0D0c
spotify   4303      chris  mem       REG        8,5    17964     921610 /usr/lib/alsa-lib/libasound_module_pcm_pulse.so


Chris

---

### Post by Pablo_F on 2011-05-22
So, it seems that jackd is already active and using your card number 0.

What is the output of:

cat /proc/asound/cards 
arecord -l && aplay -l

Above all, does rosegarden start?

---

### Post by chuning on 2011-05-23
Hi Pablo - 

Many thanks for your reply

That output is:

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd6700000 irq 46
 1 [UA3FX          ]: USB-Audio - UA-3FX
                      EDIROL UA-3FX at usb-0000:00:1d.7-2.2, full speed
chris@chris-Aspire-5736Z:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA3FX [UA-3FX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA3FX [UA-3FX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Yes, Rosegarden does start

---

### Post by Pablo_F on 2011-05-23
Hi,

Rosegarden doesn't talk to the audio card but to the jack audio server. You usually select the audio card in the setup window of Jack Control (interface field).

You can use their numbers but names are best. For example, if you want to hear Rosegarden through the UA3FX, write down:

hw:UA3FX

However, as already mentioned, Rosegarden will not make sound if you do nothing more than drawing notes or hit the piano roll. Search the internet.

Cheers, Pablo

---

### Post by chuning on 2011-05-23
Thanks Pablo - will let you know how I get on

Chris

---


---
title: "boooo --- jack is reverting to internal soundcard (control device hw:0)"
date: 2011-12-16
forum: Ubuntu Studio
---

### Post by scyntl on 2011-12-16
I have a USB soundcard, and jack was working fine until I played music with a program like audacious through the USB soundcard. (The kernel updated in the meantime too, but I've had this problem before with no kernel-update.) Now all sound in jack goes through my internal soundcard/speakers and not through my USB soundcard.  

I've closed all other programs, and I can choose to change the settings in jack to 

[INDENT]Input Device: hw:0 [HDA NVidia] OR hw:0,0 [HDA Conexant Analog] OR hw:1 [io|2] OR hw:1,0 [USB Audio] OR (default)[/INDENT]

[INDENT]Output Device: hw:0 [HDA NVidia] OR hw:0,0 [HDA Conexant Analog] OR hw:0,1 [Conexant Digital] OR hw:1 [io|2] OR hw:1,0 [USB Audio] OR (default) .[/INDENT]

I can choose, for example, hw:1,0, and hw:1,0 so that the contents of .jackdrc read 

[INDENT]/usr/bin/jackd -dalsa -r44100 -p256 -n2 -S -D -Chw:1,0 -Phw:1,0 .[/INDENT]

Hmm...I don't know if it matters, but the jack the Message dialogue shows 

[INDENT]control device hw:0 .[/INDENT]

At any rate, no matter what I choose, all sound comes through my internal card (HDA/Conexant) and never through my USB card (io|2/USB Audio). I haven't changed any settings in Jack since the last time I used jack (before I used audacious).

The output of 
[INDENT]sudo aplay -l [/INDENT]
is

**** HARDWARE PLAYBACK LIST ****
CARD 0: NVidia [HDA NVidia], DEVICE 0: CONEXANT Analog [CONEXANT Analog]
  SUBDEVICE: 0/1
  SUBDEVICE #0: subdevice #0
CARD 0: NVidia [HDA NVidia], DEVICE 1: Conexant Digital [Conexant Digital]
  SUBDEVICE: 1/1
  SUBDEVICE #0: subdevice #0
CARD 1: io2 [io|2], DEVICE 0: USB Audio [USB Audio]
  SUBDEVICE: 1/1
  SUBDEVICE #0: subdevice #0

The first time this happened to me I gave up and reinstalled ubuntu (11.10) I'd like to avoid that routine, so of course any advice would be appreciated. (If I missed a thread addressing this, please point me to it!!!) Thanks.

:confused:

(Oh, I've never figured out how to get the PulseAudio JACK Source to play through the USB soundcard. I wrote that off as a potential driver issue. . . )

---

### Post by beefheartvliet on 2011-12-16
This post might answer your question. 

[http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/](http://www.linuxquestions.org/questions/linux-hardware-18/default-sound-card-in-ubuntu-564006/)

---

### Post by scyntl on 2011-12-16
beefheartvliet> you're good!

In the meantime i was led to the same solution by
[INDENT][/INDENT][http://crunchbanglinux.org/forums/topic/9852/how-to-assign-usb-audio-as-primary-sound-device-in-alsa/](http://crunchbanglinux.org/forums/topic/9852/how-to-assign-usb-audio-as-primary-sound-device-in-alsa/) 

but your link is more indepth; so glad this is so easily fixable!

I just set bumped the snd_usb_audio index to -1 in /etc/modprobe.d/alsa-base.conf and i'm good to go!

THANK YOU!

---

### Post by beefheartvliet on 2011-12-25
A bit belated, but glad ya sorted it. I had a similar issue :-)
Just another thing you might want to know that might be in use if you use midi
is the command "a2jmidid". if you don't have it installed, then you can get it from synaptic.
It creates virtual ins and outs in the midi tab of the connections window in jack ;-)

---

### Post by scyntl on 2012-01-12
thnx again!

---


---
title: "Tascam us-122: lights on but no sound"
date: 2011-03-05
forum: Ubuntu Studio
---

### Post by Gylstar on 2011-03-05
Hello Forum! I'm new to this forum and I'm writing from Italy.

I bought this used tascam us-122, and (working VERY hard) managed to install it (or at least I think so). I followed some step-by-step guide around the web, ending with the command "usx2yloader" and modified UDEV, so now when I turn on the Pc, che USB light on the sound card is on. The problem is that, if I go to the audio preferences (the one that you obtain by clicking the loudspeaker on the bar) it shows that i have got this card, but if I select it as output, and I try to play anything, whatever I play stands still, does not play.

Do you know what my problem might be?

thank you.

Add: I tried also recording (simply with the sound recorder) and same thing: if I select my internal sound card, it starts recording. If I select the tascam, it doesn't start.

---

### Post by cchhrriiss121212 on 2011-03-05
Hi,
can you post what this shows from a terminal?
```
lsusb && aplay -l && arecord -l
```

---

### Post by Gylstar on 2011-03-05
here it is ;)

Almost forgot: I'm on Lucid.

```
gyl@gyl-desktop:~$ lsusb && aplay -l && arecord -l
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1307:0330 Transcend Information, Inc. 
Bus 001 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: USX2Y [TASCAM US-X2Y], dispositivo 0: US-X2Y Audio [US-X2Y Audio #0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
**** Lista di CAPTURE dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: USX2Y [TASCAM US-X2Y], dispositivo 0: US-X2Y Audio [US-X2Y Audio #0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```

I'm sorry it is partially in Italian. dispositivo means device, sottoperiferica means subdevice

---

### Post by cchhrriiss121212 on 2011-03-05
That all looks OK to me. Did you get any errors during the installation? And what firmware did you install? You can check the version number in synaptic package manager.

---

### Post by Gylstar on 2011-03-05
the only "alsa firmware" that I can find in synapt. is alsa-firmware-loader, version 1.0.22. The last time that I used the terminal, I installed the 0.22 version of alsa-firmware. All this following step-by-step guides.

I have been reading in a post that the problem could be in the USB ports, that are 2.0, while the device needs 1.1 ports. Is it possible? It sounds strange, since in Windows it works perfectly.

---

### Post by sgx on 2011-03-06
> **Gylstar said:**
> the only "alsa firmware" that I can find in synapt. is alsa-firmware-loader, version 1.0.22. The last time that I used the terminal, I installed the 0.22 version of alsa-firmware. All this following step-by-step guides.

I have been reading in a post that the problem could be in the USB ports, that are 2.0, while the device needs 1.1 ports. Is it possible? It sounds strange, since in Windows it works perfectly.
If it's a brand-new Tascam, the ciruit board may be different than ones that were working a couple years back. Board designers update
to new designs with reduced chip counts to save money. If it's an older one, you can google some topics where people had success, and hopefully duplicate the process. From '2009

[http://www.pps.jussieu.fr/~smimram/tascam/](http://www.pps.jussieu.fr/~smimram/tascam/)

[http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030001](http://www.premiumorange.com/la-page-web-of-phil/index.php?page=P030001)  (this one mentions the
model design change issue)

---

### Post by Gylstar on 2011-03-06
It's not 122L but simply us122. Yes I'm actually in contact with someone who is using it, but in the meanwhile i tried also to ask here :) I have been following various guides but to no success. At the present moment I'm dealing with the absence of the command "asoundconf" on lucid, do you think it is important?

---

### Post by AutoStatic on 2011-03-06
[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
And check this thread too: [http://ubuntuforums.org/showthread.php?t=1692289](http://ubuntuforums.org/showthread.php?t=1692289)
because some info on the help page is outdated.

Best,

Jeremy

---

### Post by Gylstar on 2011-03-06
Ok thank you :) so you mean that I should download and use alsa-firmware 23 and for the usx2y use the one that comes with it? So (I'm asking just to be sure) i would have to substitute some path in the guide?

---

### Post by Gylstar on 2011-03-06
I did it all again, from the beginning, and again I succeded (easily, i would say) in activating the card.

It is also plugandplay without modifying UDEV.

But still no soud, nor input nor output.

---

### Post by sgx on 2011-03-07
In Jack Connect (qjackctl) on the middle right side, 

Input device  >
Output Device  >

is the Tascam listed when you click the  >
?
Cheers

---

### Post by Gylstar on 2011-03-07
Yes it is, but this is what I get when i select it and press start (settings are all correct, i checked it with a guide).

```
14:31:30.304 Startup script...
14:31:30.305 artsshell -q terminate
sh: artsshell: not found
14:31:30.706 Startup script terminated with exit status=32512.
14:31:30.706 JACK is starting...
14:31:30.706 /usr/bin/jackd -v -P86 -m -dalsa -dhw:2 -r44100 -p1024 -n2 -H -M
14:31:30.717 JACK was started with PID=1991.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    3033519
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:2|hw:2|1024|2|44100|0|0|hwmon|hwmeter|-|32bit
control device hw:2
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
ALSA: cannot set hardware parameters for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x8b644a8 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
server thread back from poll
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
14:31:30.957 JACK was stopped successfully.
14:31:30.957 Post-shutdown script...
14:31:30.957 killall jackd
jackd: no process found
14:31:31.375 Post-shutdown script terminated with exit status=256.
14:31:32.854 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by sgx on 2011-03-07
Have you tried using your software and the unit at 48000 instead of 44100? Or test with another linux live media?

Tested in windows?  I read some of these are damaged from users switching
phantom power on/off, or inserting/removing mics, when the unit is powered on. Supposedly the circuits are not buffered properly, and subtle things fry.
Cheers

---

### Post by Gylstar on 2011-03-07
> **sgx said:**
> Have you tried using your software and the unit at 48000 instead of 44100? Or test with another linux live media?

Tested in windows?  I read some of these are damaged from users switching
phantom power on/off, or inserting/removing mics, when the unit is powered on. Supposedly the circuits are not buffered properly, and subtle things fry.
Cheers

did everything :) nothing changes. Actually, I'm giving up, and giving the card back to the previous owner, that is so kind to refund me. Too much "work", too much time spent unusefully just to have some fun doing some home recording. Going to try a card that works properly. Any advice?

---

### Post by sgx on 2011-03-07
On a desktop, I use maudio 24/96 pci, no problems, envy24control is a mixer app for the envy24 sound chipset, which many maudio and terratech cards use. So looking for devices using that chip is good, and there are usb devices from maudio with that. After a long effort, emu 0202 and 0404 are working, a Yamaha Audiogram 6 is mentioned recently, but has no midi, there are quite a few firewire users here 

[http://www.ffado.org/](http://www.ffado.org/)

The recent forum pages have topics with information on quite a few products.
Cheers

---


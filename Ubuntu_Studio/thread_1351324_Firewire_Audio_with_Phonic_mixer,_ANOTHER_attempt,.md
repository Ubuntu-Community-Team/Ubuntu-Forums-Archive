---
title: "Firewire Audio with Phonic mixer, ANOTHER attempt, please help!"
date: 2009-12-10
forum: Ubuntu Studio
---

### Post by mrufino1 on 2009-12-10
I just installed ubuntustudio to my old dell latitude d505, another attempt to get ubuntustudio working for me, I really want to stop using windows for audio. I have the phonic firewire24MKII mixer, and in the past I have gotten it to work with ubuntu but not in a while. 
I have edited the permissions file to allow raw1394 access by the audio group, of which I am a member.
I have edited the security limits file to allow rt priority 99, nice -10, memlock 256

Here's the jack output, it is the same whether using my built in 4 pin firewire port or my external TI firewire PCMCIA card:

 13:46:19.888 JACK is starting...
13:46:19.889 /usr/bin/jackd -v -R -P70 -dfirewire -dplughw:0 -r44100 -p1024 -n3 -i16 -o2
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
13:46:19.902 JACK was started with PID=2003.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot lock down memory for jackd (Cannot allocate memory)
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
new client: firewire_pcm, id = 1 type 1 @ 0x8092f58 fd = -1
new buffer size 1024
starting server engine shutdown
freeing shared port segments
stopping server thread
00380435771:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
no message buffer overruns
13:46:19.962 JACK was stopped successfully.
13:46:19.963 Post-shutdown script...
13:46:19.964 killall jackd
jackd: no process found
13:46:20.374 Post-shutdown script terminated with exit status=256.
13:46:22.080 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I can get this mixer to work well in puppy linux on the same computer, but in puppy you run as root, so I am sure it is a permission thing.
If anyone has any ideas I would very much appreciate the help. 

The ubuntustudio install is 9.10, installed via regular ubuntu then addidng the ubuntustudio packages through synaptic.

Thanks in advance.

---

### Post by AutoStatic on 2009-12-11
```
cannot lock down memory for jackd (Cannot allocate memory)
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
start poll on 3 fd's
loading driver ..
JACK: unable to mlock() port buffers: Cannot allocate memory
JACK: unable to mlock() port buffers: Cannot allocate memory
```

How does your /etc/security/limits.conf look like?

---

### Post by mrufino1 on 2009-12-11
Okay, I posted the output of security limits, then realized I had memlock set for 512, not 512000, big difference. So that error is gone. However, still no starting of jack, here's the new JACK output:

09:28:47.396 Startup script terminated with exit status=32512.
09:28:47.396 JACK is starting...
09:28:47.397 /usr/bin/jackd -v -R -P89 -dfirewire -dhw:0 -r44100 -p1024 -n3 -i16 -o2
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
09:28:47.412 JACK was started with PID=1938.
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_freebob.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: firewire_pcm, id = 1 type 1 @ 0x82cbf70 fd = -1
new buffer size 1024
00199983452:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
no message buffer overruns
09:28:48.371 JACK was stopped successfully.
09:28:48.372 Post-shutdown script...
09:28:48.373 killall jackd
jackd: no process found
09:28:48.785 Post-shutdown script terminated with exit status=256.
09:28:49.618 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


While we're at it, here is the permissions file, /etc/udev/rules.d/65-permission-raw.rules

 KERNEL=="raw1394", GROUP="audio"
 KERNEL=="1394", GROUP="audio"
 KERNEL=="dv1394", GROUP="audio"


I had also previously had each line looking like 
KERNEL=="raw1394" , OWNER="root" , GROUP="audio" , MODE="660"
Same output

One thing I noticed is that my option for hardware in qjackctl are hw:0 and plughw:0, I think those are both referring to my internal soundcard, not the firewire mixer. The firewire mixer is plugged into my TI pcmcia firewire card, which was plugged in on reboot, so it should have been picked up, right? I notice in puppy, when I have this working, jack indicates another hardware choice (if I remember correctly). Also, I remember 3 things running, 1394, dv1394, and raw1394. If I modprobe on this setup, dv1394 and raw1394 are no problem, but it says it cannopt load module 1394. 

Any ideas?!!

Thanks.

---

### Post by AutoStatic on 2009-12-11
You should leave Interface on (default) because when using Firewire the backend changes from Alsa to FFADO so things like hw:0 and plughw:0 won't work, those are Alsa designators if I'm correct.
You're now using hw:0 apparently, that's why you probably get this error message: firewire ERR: Error creating FFADO streaming device

---

### Post by mrufino1 on 2009-12-11
Okay... 
PLugged the mixer into the onboard 4 pin firewire, and success!!!!

Now, is it possible that the onboard firewire conflicts with the card? I worry about this because my actual computer I use for music is an ibm t60 that does nto have built in firewire and I use the pcmcia card with it. I can't install ubuntu studio to that yet until I know it works. I'm going to try disabling the built in firewire on the motherboard if I can. I'll keep it all posted here. If this all works, I am very very happy!

---

### Post by AutoStatic on 2009-12-11
> **mrufino1 said:**
> Okay... 
PLugged the mixer into the onboard 4 pin firewire, and success!!!!Nice!

> **mrufino1 said:**
> Now, is it possible that the onboard firewire conflicts with the card?I doubt it, the Firewire stack is pretty generic so the stack will see both Firewire chipsets but as long as you're using one of them it should be no problem. Also, when using FFADO the Firewire device is accessed through the raw1394 module which is even more generic, actually I think FFADO does all the work so it really shouldn't matter.
What kind of PCMCIA card are you using by the way?

---

### Post by mrufino1 on 2009-12-12
The pcmcia card is a coolgear (TI chipset). However, it is not working on either of my laptops with this mixer. I have used it before, so I wonder if for some reason it is not working with this kernel? I am going to see if my firewire hard drive works with the card. It is being recognized, because it is listed in lspci. Very strange. I need to use a firewire card for my T60, which does not have built in firewire, and the t60 is my computer for music, the one that is working now (dell) is my work computer and is very old. Any idea if another firewire card might be a better match? We were theorizing tonight that the chipset in my card may be causing the issue- the dell is also a TI chipset but not the same one. I'm going to see if I can access another firewire card to see what happens.

---

### Post by trulan on 2009-12-12
If you find one that works let me know.  I also have a dell laptop that works with the onboard firewire and not with a card I have.  The card is a TI chipset and the internal is a Ricoh, so common sense says it should work with the card and not the internal, but reality says otherwise.  Plus, the mini firewire plug in the computer is partially broken and occasionally glitches.  I would feel better if I were using a regular firewire plug instead of the flimsy mini plug but I already have bought one dud card.  If I buy another card I want to be sure it will work.

---

### Post by mrufino1 on 2009-12-12
Okay trulan, that's sort of good news then, because it points to this as a firewire card issue, not my mixer or a software or permissions issue. I found a few on ebay that were cheap, I may try one of those. There is an adaptec I found, and also an older one, can't remember the brand, that was said to work with ubuntu 7.10. However, I am also wondering if the newer kernel is the issue, because puppy uses a different kernel and this card is recognized. I think...guess I'll be checking that when I have time today.

---

### Post by mrufino1 on 2009-12-14
Trulan, due to some research and finding a post of yours about irq's and such, I realzed that I needed ohci1394 in the permission-raw file in rules.d, and now on my IBM the firewire mixer is starting with the firewire card I have (and after I bought one for 5.00 on ebay today, oh well!). Now I need to actually make my t60 into a music machine and make the dell my work computer again. Still doesn't work on the dell, and although I want to know why, the dell is not intended for music anyway (1.5 ghz centrino with 512 ram). So thank you for your posts- even though they were about a slightly different issue (which I will also tweak, adding ohci to the irq file), it got me thinking. Hopefully I can transition fully to linux audio really soon.

---


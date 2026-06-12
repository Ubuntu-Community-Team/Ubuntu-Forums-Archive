---
title: "problems with firewire audio device"
date: 2008-11-15
forum: Ubuntu Studio
---

### Post by gamby86 on 2008-11-15
Hi all,

I just bought a firewire audio mixer, the "Phonic Helix Board 12 MKII" and I'm trying to use it with ubuntu...
I first tried Intrepid, but due to the known problems with realtime kernel I decided to switch back to 8.04.

Anyway... the device works well with both the distros: with a latency of about 5ms I never have xruns and I think I could do better!
But... I'm experiencing some problems with drivers (freebob/ffado) and with jack/qjackctl and with programs interfacing to them.

Frist of all: with intrepid I can correctly start both freebob and ffado, while in hardy I can only start the old freebob driver (I caught ffado from APT repo on ffado.org wesite). But this is not the main problem, I will continue to use freebob.

Second problem, the main one: if I stop jack, then restart it, qjackctl freezes and I must restart the whole system to resore it! Another strange thing is that in intrepid this doesn't happen too often, while in hardy it always freezes!

The third problem is related to two programs that use jack:
- GuitarRig (wineasio interface): i used it for about two weeks without many problems (some crashes but not very often) with intrepid. Now with hardy it crashes and makes jack to crash too.
- Hydrogen: i'm trying to interface a midi drumkit to hydrogen through an Edirol UM-1EX usb/midi interface, then play hydrogen through jack and firewire mixer. Is it possible? Whith my old Audigy PCI card I could play tracks from hydrogen but I never interfaced it through midi... Now I'm trying to connect hydrogen to jack, but without success

My PC config: shuttle XPC SG33G5M, core2duo E6550, 2GB DDR2... The firewire chip (i just made an "lspci") is: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller

I'm looking for some tips&tricks to make my firewire mixer work as well as possible... I'm going to make some records with my band!

Thank you in advance and... Sorry for my bad English! I hope you will understand me!

---

### Post by mrufino1 on 2008-11-18
I have the firewire 24mkII and just got it working partway yesterday, so let's keep each other up to date with developments. I was not aware there were problems with the real time kernel in intrepid- I installed intrepid fresh 2 weeks ago and am debating whether to go back to 8.04 or ride out the waves. I am getting much distortion from the mixer (using reaper and wineasio through the new reaper linux installer on the reaper board, which uses a self contained wine and wineasio), which goes away if I lower the master volume in reaper to-50, but that is not right so I want it to be right. I had it working yesterday afternoon, so I don't know what I did to break it. I can only get the mixer and jack to work with the freebob driver, not sure if this is right or not but that is what was working. Also, I am getting a HUGE number of xruns, causing a beep in reaper about every 5-8 seconds. I shut the network off thinking that may be the problem, but it wasn't. I will do more investigating tonight with my limited knowledge, but let's keep up to date here. I do notice jack freezing things up if I stop it in the rt kernel, I have had to reboot several times. Firefox has been causing me problems once in a while too, btu that's for another thread! Thanks!

---

### Post by Stochastic on 2008-11-18
I'm glad you're having success with the Helix Board 12.  It says on the FFADO website that it's status is Unknown: [http://ffado.org/?q=node/74](http://ffado.org/?q=node/74)  You should probably send them a message and let them know it works.

As for ffado in Hardy, I was able to get it working by compiling from source, but that's a bit of work.  If freebob is working, then you could just accept that, but ffado is the newer more featured version of freebob.  If you mean to say that qjackctl doesn't have an option for ffado in the dropdown menu, you'll need to recompile qjackctl from source - or simply start jack from the command line ```
jackd -R -dfirewire
``` then open qjackctl (or better yet, patchage) - it will realize jack is already started, then operate like normal.

The Hydrogen problem might be associated with the option in hydrogen's settings to "autoconnect to outputs" I've always found this to be a bad option when using jack and it's better to manually connect things in the patchbay of your choice.  You also need to set the sampling rates to be the same in Hydrogen as in Jack.

I can't give any advice on the GuitarRig other than you might want to use the CAPS ladspa plugins in JackRack as an alternative if you can't get GuitarRig running right in Hardy.

Now as for your main problem with Hardy freezing... I found with my Firepod that anytime I stopped jack, I would need to briefly unplug the firewire cord before attempting to restart things.  This might help with your freezing issues.  My gut tells me this stems from the design of something within the driver/firewire chain that has been looked past.  I'd also explain the experience to the FFADO developers as you let them know that you've had success with your card.

Hope this helps.

---

### Post by mrufino1 on 2008-11-19
Well, I am having success tonight thanks to a friend's help, things are working pretty well. I did need to compile a new version of jack (not a process I understandI am getting xruns still with reaper, but I think that my be that I am using an IBM T41 (1.5ghz centrino) and playing audio from the internal hard drive of my laptop, and since wine is also running there has to be a performance hit. I can't seem to plug my firewire hard drive in at the same time as the mixer, and apparently my usb2 enclosure is not working, so I'll need to get a USB enclosure sometime soon before doing any real recording. If I run ardour though, the xruns are minimal at 5ms of latency and none at all at 8ms. Almost there!

---

### Post by kayosiii on 2008-11-19
freebob is pretty broken for me under 8.10. I upgraded to ffado but was not an easy thing to do.

---

### Post by mrufino1 on 2008-11-19
freebob most definitely did not work with the phonic mixer, but ffado works great. installing ffado is fairly easy because you can do it through synaptic, but for me compiling jack was very hard. turns out the aclocal file was missing from /usr/bin. I did:
sudo apt-get install autoconf
then
cp /usr/bin/aclocal-1.10 /usr/bin/aclocal
and that made the aclocal file, then all was well. My friend found a post on this board that referred to that issue regarding another program, and it turned out to be the issue here too. That was my first compiling of anything (sadly not my own knowledge that got me there but hopefully I can understand it and help others at some point)
Thanks for the replies, I was almost ready to give up on linux music but with the new easy reaper installer and the new ffado I may be able to give up on ms music...

---


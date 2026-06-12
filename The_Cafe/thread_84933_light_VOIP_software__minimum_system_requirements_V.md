---
title: "light VOIP software / minimum system requirements VOIP"
date: 2005-11-01
forum: The Cafe
---

### Post by ubuntu_demon on 2005-11-01
Hi,

what are the minimum system requirements for VOIP?

What light VOIP software do you guys recommend ?

The target pc :
pentium 2 266 MMX
64 mb ram (if needed we'll get more ram)
runs Ubuntu breezy with icewm

thnx!

---

### Post by lorenco on 2005-11-01
Skype ..[ www.skype.com]("http://www.skype.com")

EDIT: Skype minumum requirements : 
The minimum hardware requirements are: * 400 MHz processor * 128 MB RAM * 10 MB free disk space on your hard drive * Sound Card, speakers and microphone * Internet Connection (either dial-up: minimum 33.6 Kbps modem, or any broadband

I have it running on Kubuntu Breezy (433 Celeron 256 Mb Ram...)  But give it  bash... maybe it works... Network speed ismore important than CPU ?

---

### Post by totalshredder on 2005-11-01
I doubt you'll get anywhere with skype IMHO. On a 400mhz computer with 256 RAM, I had my cpu completely used up, and things started choking up when I tried to do something else. I'm sure there's some real low resource programs you could make use of :)

Luke

---

### Post by lorenco on 2005-11-01
Well as long as you don't try to do anything else while talking... otherwise use a bigger PC. My box is good enough for educational progs for my kids (and my secondary IP Phone ...)

---

### Post by fishfork on 2005-11-08
You should try gnomemeeting, if you haven't already. I found it was much less taxing on the CPU - it ran on my old laptop, which couldn't handle skype. It's included in a default install of Ubuntu, so you'll find it in the menu.

It might take a while to get it to talk to a windows machine, but it is possible, using netmeeting or similar. I'm looking forward to the next version of GnomeMeeting which will support the SIP protocol, which means it will work with countless companies that offer cheap PC-to-phone and phone-to-PC calling. Should be better than Skype!

---

### Post by ubuntu_demon on 2005-11-09
[QUOTE=fishfork]You should try gnomemeeting, if you haven't already. I found it was much less taxing on the CPU - it ran on my old laptop, which couldn't handle skype. It's included in a default install of Ubuntu, so you'll find it in the menu.

It might take a while to get it to talk to a windows machine, but it is possible, using netmeeting or similar. I'm looking forward to the next version of GnomeMeeting which will support the SIP protocol, which means it will work with countless companies that offer cheap PC-to-phone and phone-to-PC calling. Should be better than Skype![/QUOTE]
thnx I'll give it a try. gnomemeeting is not in the menu by default in icewm but installing it is ofcourse np :)

My GF and me are both ubuntu users (I installed icewm/Ubuntu on her box).

I'm looking forward to the next version of gaim. That might offer good voice support. (gaim-vv will be merged into gaim 2.0 with a bit of luck) I hope it's gonna be light.

---

### Post by ubuntu_demon on 2005-11-11
I'm trying gnome-meeting. I think I may have a little problem with the soundcard.

It's an compaq deskpro with ES1869 soundcard.

copy paste to self :

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

---


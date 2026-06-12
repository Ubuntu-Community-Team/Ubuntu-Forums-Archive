---
title: "How do I make M audio delta 66 work on Ubuntu?"
date: 2009-11-23
forum: Ubuntu Studio
---

### Post by grastein on 2009-11-23
hello

I have bought maudio delta 66.
I searched for a soundcard that was supported under Linux! 

My computer dose not automatically recognise delta 66. I have downloaded envy24 control? 

dose anyone have any experince with this soundcard? 


Cheers!

---

### Post by barisurum on 2009-11-23
M-audio delta 66 has an ice-1712 dsp chip. This card is supported with alsa and as far as I know the support is pretty good. And yes you have to install alsa-tools-gui (envy24control is included) to control this card.

ps: if your onboard mobo sound card is recognised in the first place it may block access to the card. If you can't get sound after envy24control, try disabling the mobo sound chip in bios.

---

### Post by sgx on 2009-11-23
A few things to do:

Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

These will reveal what sound devices are seen by your system. If your Delta card is there, select it.

alsaconf is a command to get the alsa sound system to configure your soundcards, it will ask a few questions, and needs root permissions, so

sudo alsaconf

lspci  -run this command and see if the Delta is listed

lsmod  -run this command and look for snd_ice1712 in the output to see if the Delta kernel module is found.

Cheers

---

### Post by grastein on 2009-11-26
I started qjackctl and found the ">" shaped thing, but m audio was not listed? 

and in the lspci -run command i didn't see the delta 66? 


So this means that I some have to install it or how do I make my pc recognise my soundcard?'


Cheers

---

### Post by sgx on 2009-11-26
> **grastein said:**
> I started qjackctl and found the ">" shaped thing, but m audio was not listed? 

and in the lspci -run command i didn't see the delta 66? 


So this means that I some have to install it or how do I make my pc recognise my soundcard?'


Cheersmylspci output from mAudio24/96 has this:

ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

For my soundcard, the qjackctl widget has ICE1712 hw: 0,0

Also, the lsmod command has this module listed in the cluster of sound modules:

snd_ice1712

Do any of those appear for you?

Cheers

---

### Post by tgalati4 on 2009-11-26
When you type envy24control in a terminal window, what shows up?

I have that card.  It's sweet.  Look for the Omni I/O front end for it.  It contains 2 nice mic preamps and decent volume/mixer/monitor controls as well.

---

### Post by grastein on 2009-11-30
> **sgx said:**
> mylspci output from mAudio24/96 has this:

ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

For my soundcard, the qjackctl widget has ICE1712 hw: 0,0

Also, the lsmod command has this module listed in the cluster of sound modules:

snd_ice1712

Do any of those appear for you?

Cheers


In lspci i found "01:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)"

and no snd_ice1712 was not listed i lsmod command?

---

### Post by grastein on 2009-11-30
> **tgalati4 said:**
> When you type envy24control in a terminal window, what shows up?

I have that card.  It's sweet.  Look for the Omni I/O front end for it.  It contains 2 nice mic preamps and decent volume/mixer/monitor controls as well.

When typing envy24control i termnial window it replies "No ICE1712 cards found" 



cheers!

---

### Post by grastein on 2009-12-01
anyone? :D :popcorn::KS

---

### Post by sgx on 2009-12-02
> **grastein said:**
> anyone? :D :popcorn::KS
Hi, try running

modprobe snd_ice1712

and check again. This command just loads that kernel module if available.
Cheers

---

### Post by grastein on 2009-12-02
> **sgx said:**
> Hi, try running

modprobe snd_ice1712

and check again. This command just loads that kernel module if available.
Cheers

Now it replies "FATAL: Module snd_ice1712 not found."

?

---

### Post by sgx on 2009-12-02
a few things...

in the initial audio setup routine, was there a dropdown list to choose from various mAudio cards? I read where someone in a similar pickle chose the 1010lt model, and things started working.

I have also seen discussions where punctuation is different

snd-ice1712 vs snd_ice1712

a little app called aoss is sometimes helpful, not always in forseen ways, it coordinates various apps that have 'differences'

You can try those variants, and if nothing changes, you may need a different kernel, one that fully utilizes the standard ice1712 module. You can install multiples, and choose at boot time the one you want.

Maybe consider switching the card to different pci slots.

Mepis AntiX and pclinuxos Minime 2009 are 300 meg distros, that might also be worth testing, both can run as live CDs, set your bios to boot CD/DVD before hard-disk, no need to install unless you choose to. I have a Minime setup, with just audio apps, and Opera for web access, its pretty nice with m-audio 24/96.

Another thing, I have read where cost-cutting new revisions of cards once known to work, now fail, maudio 24/96 being one. If
your card is brand-new, such might be the case, and a report to the alsa devs would be a good idea. Lee Revell is perhaps the alsa team leader.
Cheers
Cheers

---

### Post by grastein on 2009-12-04
Now i am running the ubuntu 09.10 to make sure that the kernal is up to date!

I have also put the pci soundcard in another slot! but i dont see any changes? 


I think it is weird that my PC doesn't recognise the card, Is this a common problem or is it me who doing it wrong ? :D 


cheers

---

### Post by tgalati4 on 2009-12-04
Well, you may have an ice1712 sound chip, but the VIA controller is troubling.  My Delta66 card is inside an old Pentium II, 300 MHz machine with an Intel motherboard.  I run dynebolic.org live CD for my audio recording.  It's a live CD designed for live audio work--real time kernel, jack, etc.

If you have a VIA motherboard, then there may be a kernel-communication issue with it and the PCI card.

Take the card out and find another PC, preferably one with a more Intel-like chipset.

---

### Post by sgx on 2009-12-05
> **grastein said:**
> Now i am running the ubuntu 09.10 to make sure that the kernal is up to date!

I have also put the pci soundcard in another slot! but i dont see any changes? 


I think it is weird that my PC doesn't recognise the card, Is this a common problem or is it me who doing it wrong ? :D 


cheers

I don't think it is you, read this discussion, pointing to VIA chipsts as possibly the problem:

[http://www.audioforums.com/forums/showthread.php?t=1958](http://www.audioforums.com/forums/showthread.php?t=1958)

Maybe time for a new motherboard, Santa!;)

---

### Post by itzuv on 2009-12-05
[quote=grastein;8390216]I started qjackctl and found the ">" shaped thing, but m audio was not listed? 
 
and in the lspci -run command i didn't see the delta 66? 
 
 
So this means 10 k or mor

---


---
title: "Can't change instrument sound in VkeyBd."
date: 2010-11-25
forum: Ubuntu Studio
---

### Post by BD1974 on 2010-11-25
p { margin-bottom: 0.21cm; }  [SIZE=2]Hi,[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]I'm new to Ubuntu.  I can't seem to get VkeyBd (Virtual Midi Keyboard) to change the instrument sound.  I can change the instrument on the menu, but it still sounds the same.   I have installed Ubuntu 10.10 32bit, and Ubuntu Studio packages Audio, Graphics, and Video.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]I am running VkeyBd through ZynAddSubFX, and connecting everything using Jack Control.  In Jack Control Connections\Audio, ZynAddSubFX is connected to system.  In Connections\ALSA, Virtual Keyboard is connected to ZymAddSubFX.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]What am I doing wrong?[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Thanks[/SIZE]

---

### Post by JakcV on 2011-03-06
I am having the same problem too. The sound output is from the zynaddsubfx. I am able to change the sound though instrument list from zynaddsubfx but not from vkeybd. 

The piano sound synthesis from zynaddsubfx is too fake so I plan to use vkeybd, hopefully the sound is more realistic. However, it doesn't output any sound.

---

### Post by sgx on 2011-03-06
> **JakcV said:**
> I am having the same problem too. The sound output is from the zynaddsubfx. I am able to change the sound though instrument list from zynaddsubfx but not from vkeybd. 

The piano sound synthesis from zynaddsubfx is too fake so I plan to use vkeybd, hopefully the sound is more realistic. However, it doesn't output any sound.
Hi, vkeybd is just for keypresses, not sounds, so for realistic sounds, try linuxsampler, and purchase 'giga' sound sets off ebay, craigslist, misc web hits, they are very high quality. 

Zynaddsubfx has extra soundsets from cormi, William Godrey. laba170, and is designed for a wide variety of fake sounds, that
many windows/0sEX users pay big bucks for, from commercial instruments. Additive, subtractive, and formant synthesis are all there if you press the edit button. 

Festige can be used to load vsts that have their own preset management. Zebra CM, and Triple Cheese from U-he are good
magazine and free choices, as is Synth1. Cakewalks z3ta and Zebra 2.5 are excellent commercial synths with preset handling.

Reaper can be used with wineasio, to host a wide variety of free and commercial vsts, the reaper forum has some dedicated linux folks. Lots of options out there.

---

### Post by Pablo_F on 2011-03-06
For a virtual midi keyboard, I suggest you replace vkeybd with vmpk (to install it use the software center, [here the official site]("http://vmpk.sourceforge.net/")). This is not for making sounds either but it is more versatile. For example, you can create your own keyboard maps.

A very good free piano for linuxsampler is the [Maestro Concert Grand]("http://www.linuxsampler.org/instruments.html"). Pianoteq has a linux version too.

---


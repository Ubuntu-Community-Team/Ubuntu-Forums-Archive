---
title: "Things don't make sense sometimes"
date: 2007-02-12
forum: The Cafe
---

### Post by PatrickMay16 on 2007-02-12
I have three wireless network adapters: a USB thing with the zd1211b chipset, a PCMCIA one with the TI acx111 chipset, and today I just got another PCMCIA one with a ralink chipset.

The zd1211b and ralink ones have drivers supplied by the manufacturer, even released under the GPL. 
The acx111 had no driver released by the manufacturer for linux; not any kind of official support for linux at all.

The zd1211b performs very poorly, and just now after an hour of trying with the ralink one I couldn't even get it to connect. 
The acx111 works great with no messing around.

Does that make sense to you?

---

### Post by Paerez on 2007-02-12
It actually does make sense. Since the zd and ralink ones had manufacture-provided drivers, people on the linux team didn't create the driver, the company did. But for the acx card, a linux person coded their own driver from scratch.

Guess who is better at writing linux drivers?

---

### Post by PatrickMay16 on 2007-02-12
> 
 	It actually does make sense. Since the zd and ralink ones had manufacture-provided drivers, people on the linux team didn't create the driver, the company did. But for the acx card, a linux person coded their own driver from scratch.

Guess who is better at writing linux drivers?

O RLY? I guess I forgot to mention that I tried the rewrite of the zd1211 driver (rewritten by the community so they could include it in the kernel), and that barely worked at all.

---

### Post by bastiegast on 2007-02-12
Plus, the rtx00 driver is also opensource and community developed.

---

### Post by Paerez on 2007-02-12
meybe its just a crappy card then...

---

### Post by trippinnik on 2007-02-13
I dunno, I am using the zd1211rw drivers and they have been working very well.  I can now pick up like 8 access points around my apartment, network manager and WPA are working.  Do you have any specific criticisms?  Some details might actually be productive so that people can either troubleshoot it, or understand the specifics.  "it performs horribly" doesn't really say anything.

---

### Post by awakatanka on 2007-02-13
got a RT2500 and a RT61, The RT2500 s very stable atm but does use another way of WPA ( can use  /etc/network/interface for wpa )then the rest. The RT61 isn´t very stable ATM. Probably the driver isn´t stable.

---

### Post by az on 2007-02-13
I have a zd1211b and it works perfectly.

That device actually uses about five different combinations of hardware.  Although you may have the same model, there are two different chipsets and three different transmitters (I forget the actual term for it).  So, maybe some a re better supported than others?

The fact that the kernel is able to use all permutations of the hardware is impressive.  All the more it is all GPLed software.

---

### Post by PatrickMay16 on 2007-03-05
> **trippinnik said:**
>  Do you have any specific criticisms?  Some details might actually be productive so that people can either troubleshoot it, or understand the specifics. 

when I try pinging other computers, often I'll get lost packets, and often it'll just cut out when doing stuff like transferring files or loading other stuff like websites. I can sit and wait for it to start working or I can unplug it and plug it in again or unload and load the driver module to get it working at all again.
And even when it does work at all, it works slower than the TI ACX111 card that I have; 400KB/s transferring a file compared with 950KB/s.


I didn't bother including anything like that in my original post because I didn't expect to get any replies.

---


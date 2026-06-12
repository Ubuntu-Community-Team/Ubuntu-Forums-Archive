---
title: "Is it possible to increase the graphics output speed to the display?"
date: 2015-07-16
forum: Ubuntu/Debian BASED
---

### Post by Idjit_BoB on 2015-07-16
I was running Zorin 9 Lite which uses the Lubuntu 14.04 LTS kernel on my 10 year old IBM Thinkpad T42 2373 (1.7GHz Pentium M, 512MB). After a short while the RAM would be overwhelmed and the swap disk would slow things down considerably.

I installed the maximum 2GB on my laptop and the improvement was quite noticeable.

 I was pleased, but couldn't leave well enough alone. I decided to load Zorin 9 Core which uses the Ubuntu 14.04 LTS kernel. I was aware that the graphics controller may not be robust enough to keep up. It didn't.

I searched Ubuntu for information regarding manufacturer graphics drivers and quickly read through the information which was provided at the following link.

[https://help.ubuntu.com/community/BinaryDriverHowto#Identifying_Your_Video_Card](https://help.ubuntu.com/community/BinaryDriverHowto#Identifying_Your_Video_Card)

If it helps the discussion, the following information is from my T42:

 ```
wayne@wayne-ThinkPad-T42:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV200/M7 [Mobility Radeon 7500]
wayne@wayne-ThinkPad-T42:~$ sudo lshw -C video
[sudo] password for wayne: 
  *-display               
       description: VGA compatible controller
       product: RV200/M7 [Mobility Radeon 7500]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e0000000-e7ffffff ioport:3000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
wayne@wayne-ThinkPad-T42:~$ 
```

I saw that it is an ATI card, and that it is supported.

My only issue is display speed related and I have two questions.

Will installing a driver upgrade improve graphics controller output to the display?

Will it improve the display speed or is this a limitation of the hardware?

Thanks in advance.

---

### Post by howefield on 2015-07-16
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Rob Sayer on 2015-07-16
I don't use Zorin but I'm not sure it's a kernel difference.  All ubuntu DE versions that are still supported use the same kernel.  I suspect the DE.

Don't try to use other drivers from AMD.  The card's too old and they won't work because AMD doesn't support older cards for linux.  According to this ...

[https://help.ubuntu.com/community/RadeonDriver#Supported.2C_but_Hardware_is_Too_Old_for_Unity](https://help.ubuntu.com/community/RadeonDriver#Supported.2C_but_Hardware_is_Too_Old_for_Unity)

... it'll work but you have no 3D hardware accelerated video.  I.e. the CPU will be pushing a lot of those pixels around instead of the graphics card.

I'd recommend Lubuntu or Xubuntu ... Zorin support is terrible from what I see of their forum, I wouldn't touch it ... and unfortunately it'll still have trouble with HD video playback.

---


---
title: "QEMU and IRQL NOT LESS THAN OR EQUAL Error"
date: 2009-04-26
forum: Virtualisation
---

### Post by coldReactive on 2009-04-26
When ***_trying to install_*** Vista (The OS CD that came with my computer) in QEMU... I get the error mentioned in the title, the full title of the error is DRIVER_IRQL_NOT_LESS_OR_EQUAL, this is on the CD right after the Windows is loading setup files or whatever.

Host Machine is Ubuntu 9.04 (No dual boot with Windows, as I want to emulate windows in QEMU to get past dual booting.)

It's a Gateway DX4200-UB101A.

---

### Post by coldReactive on 2009-04-27
Oh and just so you know, the STOP errors vary by what I do.

Exa: If I take out my USB Thumb Drive,
STOP: 0x0000001E

If I leave the USB Thumb Drive in or if I have it set to 1 core instead of 3 cores,
STOP: 0x000000D1

[img]http://i39.tinypic.com/2061wcn.png[/img]

---

### Post by coldReactive on 2009-04-27
Those of you who do not want to go searching for specs...

My machine (x86_64) is as follows:

AMD Phenom&#8482; X3 8400 Triple-Core processor
* Each core operates at 2.1 GHz
* 2 MB L3 cache
* 3600 MHz system bus

AMD RS780 Chipset consisting of
* Northbridge: RS780
* Southbridge: SB700

RAM
* 6 GB (6144 MB) 667 MHz DDR2 SDRAM (two 2048 MB and two 1024 MB modules)

Harddrive
* 500 GB 7200 RPM SATA II hard drive

Audio/Video
* ATI HD 3200 Integrated (I believe with 256-512 MB of Video RAM)
* Integrated ALC888S HD audio codec 7.1

I have set qemu to give out 2047 MB of RAM (But it takes around 3 GB of RAM according to top; I have 16 GB Swap under Ubuntu 9.04, and I need this much RAM so I can run certain programs like full featured games that take up 200+ MB of RAM alone with one client.)

Windows XP Home Edition (x86) install takes about 3-6 hours to complete (With a COM+ Error during installation) in this qemu setup under Ubuntu 9.04.

Edit: Finally finished installing XP (About 8-9 hours total) and now it can't start Windows XP, it just blue screens or freezes.

---

### Post by coldReactive on 2009-04-30
Just so you know, ReactOS can install and boot fine in QEMU. The problem is, is that it goes so slow, it's unbearable!

---

### Post by DaveAtFraud on 2009-05-20
Were you ever able to install Vista under qemu?  I had it working for a while on a very custom CentOS installation (2.6.28.7 kernel from kernel.org, latest versions of qemu, SDL built locally).  Unfortunately, I wanted to get Windows 7 RC working too so I built a newer kernel, etc. and now W7 works as does Server 2008 but I keep getting the STOP:0x000000A5 BSOD with both a new Vista install and using Vista images that worked before I rebuilt.  I've also tried re-creating the environment that used to work but now that doesn't even work.

I have posted some question over at the qemu forums but have yet to get any answer.

Cheers,
Dave

---

### Post by coldReactive on 2009-05-20
I wasn't ever able to get it installed under qemu.

So I went to use vbox instead.

---


---
title: "Reloading PAN-P7"
date: 2010-03-13
forum: System76 Support
---

### Post by Nomadin on 2010-03-13
I need to reload Ubuntu on my laptop.  I messed up my installation playing around too much.  Usually that is not an issue as I have installed Linux on many machines, but I am having a tough time with this laptop.  As I indicated in the subject it is a PAN-P7 with stats as follows:

[LIST]
[*]15.6" HD+ LED Display with Super Glossy Surface (1600 x 900)
[*]Graphics ATI Mobility Radeon HD 4570 Graphics with 512MB GDDR2 Memory
[*]Hard Drive 500 GB 7200 RPM SATA II
[*]Memory 4 GB – DDR3 1066 MHZ 2 DIMMs
[*]Processor Core i7-720QM Processor ( 45nm, 6MB L3 Cache, 1.60GHz )
[*]Wireless Intel Wi-Fi Link 5100 - 802.11A/B/G/N Up to 300 Mbps
[/LIST]

The reloading instructions at [http://www.knowledge76.com/index.php/Restoring_Your_System](http://www.knowledge76.com/index.php/Restoring_Your_System) are pretty out of date.  They still list reinstalling 9.04 and the System76 driver information only goes to 8.04.

I have only been successful in booting the Kubuntu 10.04 alpha 3 CD.  All of the others that I have tried will not get to the desktop (Ubuntu 9.10, Kubuntu 9.10, Mint 8, Mint 8 KDE).  I have also tried the safe graphics options and installing directly from the CD rather than going to the live CD's desktop.

Kubuntu 10.04 booted and let me install, but would not load on reboot.  It hangs on the Ubuntu screen.

I am assuming that I will need to OEM option to load some drivers, but I don't know what format the CD must be in.  I have downloaded the .deb version of the System76 drivers, but don't know what to do with them if my system won't boot.

Any help or instructions that you can post will be greatly appreciated!

---

### Post by thomasaaron on 2010-03-15
Please contact me via email.

support...at...system76...dot...com

---

### Post by Nomadin on 2010-03-15
> **thomasaaron said:**
> Please contact me via email.

support...at...system76...dot...com

Thanks!  I sent the information via email right after I posted here.

If anyone is curious, I do have Kubuntu 10.04 alpha 3 running at this time.  The hang up on boot was caused by grub2 and the splash screen.  When I removed that from the config, it booted right into KDE.

Most everything appears to be working.  The battery monitor seems accurate, which I think that someone mentioned as an issue with KDE.  Suspend has worked most of the time, but this last time I tried it, the laptop did not fully suspend.  It blanked and locked the screen, but the fan stayed running.

Interesting to play around with anyway.

---


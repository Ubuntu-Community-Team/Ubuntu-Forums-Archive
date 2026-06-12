---
title: "Sun Blade 2000 + Xorg not working"
date: 2007-11-03
forum: Sun Sparc Users
---

### Post by joeyalex on 2007-11-03
Hello Everyone,

I'm not new to linux, but I am new to Sparc machines. I have a Sun Blade 2000 that I'd really like to use as a workstation, with Xorg on it. I'm trying to use Ubuntu 7.10. The machine has an XVR-100 PCI card, which is the Sun version of a radeon 7000 from my understanding.

So far, I've installed the server portion from the CD, which works fine in console mode. Next, I installed ubuntu-desktop, and then proceeded to lose a whole day of my life trying to make it work.

Initially, I had a "No Screens Found" error. I was able to fix this by moving the card to a different PCI slot. After doing this, the radeon driver was able to find the card.

When Xorg starts up, the screen flashes like it is going to work, then it comes back on with a bunch of faint white lines running down the monitor. This situation persists until I reboot the machine. The OS continues to run in the background. It gets kicked back to console mode, but the video never returns. The monitor reads that the mode is in sync, so it appears that the bad display is actually coming from the card.

Looking at the logs, the driver does the initial setup, mmaps, and then unloads the driver with no real explanation as to why. It doesn't really give any error messages. There are some messages in the dmesg log about an unknown cmd on /dev/fb0. This is the only real error I've seen. 

I've tried every option I can think of. I'm using the radeon driver. I've tried ati, vesa, vga, sunffb..pretty much all of them. I've tried UseFBDev, noAccel, forcing the bus to PCI...all kinds of things.

I tried Debian 4.0 on the machine and got the exact same results. Solaris 10 works ok. I'm at a complete loss with this thing. It detects the card, but it is doing something wrong to it which is killing the video. I tried downgrading the video driver three releases of ubuntu back, with the exact same results.

Anyone have any ideas??

Thanks in advance!

---

### Post by drosky on 2007-11-03
This is a shot in the dark, and may totally not help, but FWIW, I have several older sun blade 150's that have onboard ATI Rage XL graphics chips.  This is totally different than what you have, but what's common is that xorg didn't work when I installed Linux (Debian Sarge, and Ubuntu LTS 6.06).  After searching around, someone had figured out that the xorg ATI driver was not detecting/setting the reference clock correctly on the chip and an option, "reference_clock" had to be included in xorg.conf to do this, after which everything worked fine.

It may be something totally different, but the suggestion is if you still have Solaris 10 on the machine, you might want to boot it and use its X configuration utility (fbconfig or some other similar utility, or looking at logs) to see if it's possible to find out what the correct configuration is for the card.  I suspect whoever figured it out for the ATI Rage chips might have taken a similar approach.

---

### Post by jchow on 2008-01-11
Hi, I have the same problem.  Is anyone has updated information on that problem?

many thanks,

---


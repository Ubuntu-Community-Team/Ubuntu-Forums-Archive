---
title: "Leopard Extreme Freezing"
date: 2011-12-19
forum: System76 Support
---

### Post by sgy on 2011-12-19
I use the Leopard Extreme at work and recently it has begun freezing.  When this happens I lose all control, and have to manually reboot.

To diagnose the problem I plan to do a live boot from a usb stick and run a memory check.  I have never done this before.  How do you advise me to proceed?  Is there a particular log file you would like to see for diagnostic purposes?  Are there any other diagnostics I should run?

The system is under warranty.

As I said this is my work machine and it is very important that I have it up and running again as soon as possible.

Below are some of my specs.  (Note that my Ubuntu Forum signature may indicate a different machine.  It is the Leopard Extreme that is problematic.)

Thanks,

Sam

==

Leopard Extreme  Core i7 960 3.20 GHz L2 8 MB QPI 4.8 GTs - 4 Cores with  Hyperthreading 
24 GB - 6 x 4 GB - Corsair Vengeance Triple Channel DDR3 - 1600 MHz

1 GB nVidia GeForce GTS 450 
300 GB Intel 320 Series SATA II 3 Gb/s Solid State Disk Drive CD-RW  / DVD-RW Dual Layer LightScribe Drive Logitech Desktop MK200

Ubuntu: Oneiric Ocelot

==

---

### Post by BC59 on 2011-12-19
Did you install the proprietary drivers for your graphics card?

---

### Post by sgy on 2011-12-19
I did not install any drivers for the graphics card.

I do not know what drivers System76 installed.

Thanks.

---

### Post by BC59 on 2011-12-19
I'm not sure but I think it's using the basic Linux drivers. So you could try installing the NVIDIA drivers. From a terminal CTRL+ALT+T run these 3 separate commands:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```

---

### Post by sgy on 2011-12-20
I tried to run Memtest from the GRUB menu and received the following error.

error: too small lower memory 0x99100 > 0x8f000

What does this mean?

I am now running Memtest from an Ubuntu live boot, and after almost half of a pass I have seen no errors.

How long should one let Memtest run?

I have not tried installing the drivers mentioned earlier.  I wanted to check the hardware first.

Thanks.

---

### Post by isantop on 2011-12-21
That looks like a bug in the included version of MemTest. You can get a live CD of the latest version (4.20) [here](http://memtest.org).

---


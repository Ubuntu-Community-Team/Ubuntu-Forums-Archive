---
title: "Motherboard boot times"
date: 2010-06-22
forum: The Cafe
---

### Post by JohnnyC35 on 2010-06-22
hey, I was wondering if anyone knows of sites that has reviews or timings of how long it takes motherboards to boot from On Button to when the OS is about to boot. With Ubuntu dropping it's boot time I was thinking that if there was a 1 or 2 second booting mobo then it would be almost like an instant on.
A few seconds is a few seconds, my computer is on most of the time anyways, but I thought it would be interesting to see if they time motherboards now. I haven't seen such reports.

---

### Post by cguy on 2010-06-22
Check out coreboot. It's a very small Linux kernel which replaces the BIOS and takes you to the OS's boot very fast.
It works on a limited number of mobos, though.

Proprietary (default) BIOSes are so slow at boot because they have to be prepared for any kind of OS you may want to run.
Many of the tests and initializations are repeated by a modern OS at boot, so go figure the waste of time!

---

### Post by ubunterooster on 2010-06-22
So that's where LinuxBIOS went!

[http://www.coreboot.org/Supported_Motherboards](http://www.coreboot.org/Supported_Motherboards)

---

### Post by BuffaloX on 2010-06-22
I read about Asrock Instant boot some time ago, and it seems to be a very serious attempt to improve BIOS boot times.

How well it works in real life I don't know, how much of BIOS boot time is spent just waiting for drives to spin up, even if those drives are completely irrelevant for booting?
How much time is wasted initiating PS2, serial, parallel, floppy and ata ports? Detecting RAID arrays that are not there, or checking if I have a CD/DVD inserted? Configuring on-board audio, dual LAN ports, checking fan speeds, cpu temps...

The list goes on and on,
I'm pretty sure the BIOS could boot in a second, if it didn't have to do all these stupid things for every single boot.

I still need the capacity of a real hard drive, Is it possible to make the BIOS completely ignore any drive not used for booting?
If this was the case I would totally buy an SSD for my boot partitions.

It's cool Ubuntu loads really fast now, but the BIOS boot time suck big time.

---

### Post by JohnnyC35 on 2010-06-22
hmm. interesting. will look into this LinuxBIOS more :)

---

### Post by cascade9 on 2010-06-26
I have never seen any tests, anywhere, that included how long it took for the BIOs to initialise.  

> **BuffaloX said:**
> How well it works in real life I don't know, how much of BIOS boot time is spent just waiting for drives to spin up, even if those drives are completely irrelevant for booting?
How much time is wasted initiating PS2, serial, parallel, floppy and ata ports? Detecting RAID arrays that are not there, or checking if I have a CD/DVD inserted? Configuring on-board audio, dual LAN ports, checking fan speeds, cpu temps...

The list goes on and on,
I'm pretty sure the BIOS could boot in a second, if it didn't have to do all these stupid things for every single boot.

You do know that you can, in most cases, turn off all the junk you are not using? I always turn of serial, parallel and floppy ports. I set the hard drive/s/optical drive so that they dont auto detect, etc. 

It doesnt make a huge difference, but it does help. 

BTW, I've got 2 systems that in a lot of ways are very similar- a 790X chipset MSI and a 770 chipset gigabyte. The MSI takes ages to initialise the BIOS, the gigabyte is within one second. They have different BIOS chips (MSI use AMI, gigabyte use award) and that might well be part of the reason why. 

Then again, it could just be that the BIOS on the MSI is craped out somehow, its given me all sorts of trouble. Even flashing the BIOS for a newer version didnt help. :|

---


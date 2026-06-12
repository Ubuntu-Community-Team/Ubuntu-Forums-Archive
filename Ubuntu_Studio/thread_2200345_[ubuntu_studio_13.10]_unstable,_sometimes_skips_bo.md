---
title: "[ubuntu_studio 13.10] unstable, sometimes skips bootloader, freezes all the time"
date: 2014-01-18
forum: Ubuntu Studio
---

### Post by junglistric on 2014-01-18
Hello,

After several attempts I was finally able to do a fresh install of 64 bit Ubuntu Studio on single HDD.  After and if it boots up, I'm unable to really do much of anything within the OS, as it hangs every time, usually when accessing the web i.e. updates, etc.

I can post any additional information if anyone is able to lend a hand.  I have tried unplugging the rest of my HDDs and unused peripherals (I have 2 other windows 8 partitions/drives installed) to no avail.

Thanks,
Eric

---

### Post by bcschmerker on 2014-01-18
What core system hardware, in terms of CPU and chipset?  I was never able to get LinUX Kernel Family 2.6.x-rt to run stably on the Advanced Micro Devices® Athlon 64® X2 5600+ under Ubuntu® 8.04.x-LTS or 10.04.x-LTS (constant panics), whereas it ran without panic or oops on a VIA® C7-D.

---

### Post by junglistric on 2014-01-18
I have an intel core2duo e6850, nvidia nforce 650i.

---

### Post by dennis13 on 2014-01-19
This could also be a hardware failure. I once had a notebook which after several years suddenly began to freeze upon the slightest movement.

Just to be sure I'd first try booting a non-rt kernel. If the problem doesn't go away I'd try booting a Live CD of Debian stable (older than Ubuntu) und Fedora (newer than Ubuntu).

Best, Dennis

---

### Post by cub on 2014-01-20
> **junglistric said:**
> After several attempts I was finally able to do a fresh install of 64 bit Ubuntu Studio on single HDD.
What caused you having to do several attempts to install?

That makes me wonder if the installation media or the downloaded iso was damaged in some way. Did you check the md5sum before installing?

---

### Post by junglistric on 2014-01-20
I didn't check the integrity of the burned iso disc.  The reason for multiple attempts was due to the install hanging on the splash page with the spinning circle.  It stayed like that for an entire night.  I had also tried to install via USB, with similar problems.  The current install was from a burned iso disc though.  I guess I can try to check the disc for errors, but I don't think that is the source of the problem.

---

### Post by junglistric on 2014-01-20
> **dennis13 said:**
> This could also be a hardware failure. I once had a notebook which after several years suddenly began to freeze upon the slightest movement.

Just to be sure I'd first try booting a non-rt kernel. If the problem doesn't go away I'd try booting a Live CD of Debian stable (older than Ubuntu) und Fedora (newer than Ubuntu).

Best, Dennis


I do suspect the HDD itself.  I have been booting the non low-latency kernel.  I can try booting a live CD as well thanks.

EDIT - It could very well be the USB wireless adaptor - ubuntu might not like it.  I will try to install the wireless PCI card drivers.

---

### Post by dennis13 on 2014-01-20
Just wondereing, why do you suspect the wireless adaptor?

Dennis

---

### Post by cub on 2014-01-21
> **junglistric said:**
> I didn't check the integrity of the burned iso disc.  The reason for multiple attempts was due to the install hanging on the splash page with the spinning circle.  It stayed like that for an entire night.  I had also tried to install via USB, with similar problems.  The current install was from a burned iso disc though.  I guess I can try to check the disc for errors, but I don't think that is the source of the problem.
Maybe not, though I had similar problems with earlier installations which then worked just fine after a new download of the iso and creation of USB stick. Still, it could be something else hardware related as you mentioned.

---

### Post by junglistric on 2014-01-21
> **dennis13 said:**
> Just wondereing, why do you suspect the wireless adaptor?

Dennis


It sometimes does not boot with the adaptor plugged in.  When I plug it in after it boots, it will access the internet and freeze shortly thereafter.

---

### Post by dennis13 on 2014-01-21
hm, okay makes sense.

---

### Post by eric41 on 2014-01-25
I've had a similar problem in 12.04, traced mine to a faulty drive.  Would also sometimes cause a 'drunken mouse' symptom.

---


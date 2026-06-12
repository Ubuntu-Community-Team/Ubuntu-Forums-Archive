---
title: "HD not found during Win XP Install"
date: 2008-02-08
forum: System76 Support
---

### Post by intrepidx on 2008-02-08
Hello,

As of today, I am the happy owner of a system76 laptop with the following specs:

1 x Serval Performance (SER-P3) = $1,755.00
       Bluetooth Bluetooth
       Extra AC Adapter no extra AC adapter
       Extra Battery no extra battery
       Hard Drive 200 GB 7200 RPM SATA
       Hardware Warranty 1 Yr. Ltd. Warranty and Technical Support
       Laptop Bag Deluxe Notebook Bag
       Memory 4 GB - 2 x 2 GB DDR2 667 MHZ
       Operating System Ubuntu 7.10 64 Bit (Gutsy Gibbon) Linux
       Optical Drive CD-RW / DVD-RW
       Portable Flash Drive no flash drive
       Processor Core 2 Duo T7700 2.4 GHz 800 MHz FSB 4 MB L2
       Wireless 802.11 agn

All day has been like Christmas morning for me. :)  For general usage of the machine, however, I would like to dual boot XP and Ubuntu.  My approach is to completely wipe out the existing Ubuntu install, install XP, and then rely on Ubuntu to repartition correctly to end up with a laptop that can do absolutely everything I need.

When starting the XP install, it states "Setup did not find any hard disk drives installed in your computer."  Ubuntu works great, there is no indication of an actual hard disk problem.  The error (with candidate solutions) is described here:

[http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/](http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/)

It seems like it's potentially a driver issue (relating to SATA?  motherboard?), but I'm not clear on exactly what drivers I need, or how they should be supplied to Win XP; that is, even if I knew the correct drivers, what media could I install them with that would be detected by the Win XP installer?

I do understand that Windows installations fall outside the scope of support offered by system76; however, if anyone here is kind enough to share any insights that might help, I would be extremely grateful.

Thank you to the system76 folks for an exceptional laptop at a great price!

Best regards,

Dave.

---

### Post by compholio on 2008-02-09
> **intrepidx said:**
> ...
It seems like it's potentially a driver issue (relating to SATA?  motherboard?), but I'm not clear on exactly what drivers I need, or how they should be supplied to Win XP; that is, even if I knew the correct drivers, what media could I install them with that would be detected by the Win XP installer?
...

Well, normally I would suggest you download the SATA driver and load it on a USB key but I also have a SERP3 and noticed that there is no option in the BIOS to load USB devices as if they are floppy disks.  So, you have a couple options:
1) Find an updated BIOS that supports USB floppy emulation and put the SATA driver on a USB flash disk
2) Create a "slipstream" XP cd that includes the driver

To find the appropriate driver you will want to load up a terminal and run lspci, you should see something like (probably exactly):
Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)

So, you get the driver from Intel's website and do (1) or (2).

---

### Post by saxamo on 2008-02-09
My Two cents:

I've been trying to get XP on my Dater (daru2) since the holidays and I never really got it to work. The drivers you need are more than likely on the driver CD that came with the laptop. I used[ nLite]("http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml") to burn a few copies of XP with different driver files, but none of the discs recognized my hard drive. I don't know if this is due to me putting the wrong driver files on the disk, or what.

So all in all just be careful, and let us know how you fare!

---

### Post by riseringseeker on 2008-02-09
> **intrepidx said:**
> Hello,

As of today, I am the happy owner of a system76 laptop with the following specs:

1 x Serval Performance (SER-P3) = $1,755.00
       Bluetooth Bluetooth
       Extra AC Adapter no extra AC adapter
       Extra Battery no extra battery
       Hard Drive 200 GB 7200 RPM SATA
       Hardware Warranty 1 Yr. Ltd. Warranty and Technical Support
       Laptop Bag Deluxe Notebook Bag
       Memory 4 GB - 2 x 2 GB DDR2 667 MHZ
       Operating System Ubuntu 7.10 64 Bit (Gutsy Gibbon) Linux
       Optical Drive CD-RW / DVD-RW
       Portable Flash Drive no flash drive
       Processor Core 2 Duo T7700 2.4 GHz 800 MHz FSB 4 MB L2
       Wireless 802.11 agn

All day has been like Christmas morning for me. :)  For general usage of the machine, however, I would like to dual boot XP and Ubuntu.  My approach is to completely wipe out the existing Ubuntu install, install XP, and then rely on Ubuntu to repartition correctly to end up with a laptop that can do absolutely everything I need.

When starting the XP install, it states "Setup did not find any hard disk drives installed in your computer."  Ubuntu works great, there is no indication of an actual hard disk problem.  The error (with candidate solutions) is described here:

[http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/](http://www.raymond.cc/blog/archives/2008/01/21/install-xp-setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/)

It seems like it's potentially a driver issue (relating to SATA?  motherboard?), but I'm not clear on exactly what drivers I need, or how they should be supplied to Win XP; that is, even if I knew the correct drivers, what media could I install them with that would be detected by the Win XP installer?

I do understand that Windows installations fall outside the scope of support offered by system76; however, if anyone here is kind enough to share any insights that might help, I would be extremely grateful.

Thank you to the system76 folks for an exceptional laptop at a great price!

Best regards,

Dave.

Is there something particular you need to do that you have to have XP installed as a separate partition?  

After much wailing and gnashing of teeth, I was not able to successfully run Rosetta Stone in Linux under Wine (though from googling, I should have been able to - no doubt some error on my part).  

My solution was to load XP as a VM, and things work great now - probably "boots" faster this way than if it were a separate partition/OS as well, and of course, there is no need to restart the computer to get Linux up again, as it never shut down - for me a perfect solution.

You may want to look at Innotek (available via repositories), or something similar if running a VM would do what you need XP for.

---

### Post by xc3RnbFO8P on 2008-02-09
[Windows XP do not support AHCI]("http://en.wikipedia.org/wiki/Serial_ATA")


In bios disable AHCI

---

### Post by compholio on 2008-02-09
> **Ringi said:**
> [Windows XP do not support AHCI]("http://en.wikipedia.org/wiki/Serial_ATA")


In bios disable AHCI

The SERP3 has AHCI disabled from the factory.

---

### Post by xc3RnbFO8P on 2008-02-09
(Mistake)

---

### Post by reh4c on 2008-02-10
I can confirm that WinXP can be installed on the Daru2 by disabling AHCI in the BIOS.  I can't speak for other models.  I'll also add that WinXP64 is a royal pain in the a$$ to get the drivers loaded properly.  Vista may work better:roll: If power management can be fixed (and possibly the webcam and fingerprint reader working), Ubuntu is the way to go.  Here's hoping for a fabulous Hardy release!!!

---

### Post by intrepidx on 2008-02-10
Hello again,

Disabling AHCI did the trick.  Mind you, even after installing the provided drivers, Windows XP will still fail to boot if AHCI is turned back on.  Simple solution:  leave it switched off. :)  I haven't noticed any consequences from having AHCI disabled on either Windows or Linux.

I'm not really a hardware person, so your comments were very helpful.  Thank you!

Dave.

---

### Post by asmiller-ke6seh on 2008-02-11
> **intrepidx said:**
> Hello again,

Disabling AHCI did the trick.  Mind you, even after installing the provided drivers, Windows XP will still fail to boot if AHCI is turned back on.  Simple solution:  leave it switched off. :)  I haven't noticed any consequences from having AHCI disabled on either Windows or Linux.

I'm not really a hardware person, so your comments were very helpful.  Thank you!

Dave.

You may want to thank Ringi by clicking on the Hero's Star Medal in the lower right hand corner of the post that made the difference for you.

The THANKS function is fairly new in this forum, and it is a great way to make your Thank You a little more long-lasting.

---


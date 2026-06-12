---
title: "LTSP Thin clients bot with very low resolution"
date: 2008-11-16
forum: Server Platforms
---

### Post by JGSD on 2008-11-16
I've had an Edubuntu 7.04 server running LTSP for a bunch of Wyse Winterm (booting by PXE) thin clients for a while. Recently, I decided to test one of Wyse's new "Zero Clients" -- specifically a V00LE. However, I was never able to get it to boot at higher than 1024x768 on the Samsung 740B 17" monitors we use, even those the Winterms are working fine at the same resolution.

Anyway, I decided that I'd set up a new server running the latest Ubuntu 8.10 and install the "ltsp-server-standalone" package. The LTSP setup went smoothly and the Winterms boot at 1280x1024. However, the V00LE now only seems to be able to do a maximum of 800x600! In other words, it has gotten worse!

According to the Wyse Zero Client Specs [(PDF Link)]("http://www.wyse.com/products/hardware/thinclients/V00LE/Wyse_V00LE.pdf"), the V00LE is supposed to be capable of 1600x1200@85Hz in 32 bit colour, and I know that these Samsung 740B monitors can handle 1280x1024.

I have spent some time reading the various forums and have found that almost everyone is recommending adding an X_MODE_0 line with the desired resolution in lts.conf. I have also read the various postings from people who have said that it seems as though lts.conf is being ignored, the ones that say a new one should be made in /var/lib/tftboot/ltsp/i386/ and the ones who say that the ltsp-update-image command has to be run after each change to lts.conf...........  well, I have done all of these things, I can't seem to affect the resolution at all, even when I try to bring it down further to 640x480.

Just for the record, I tried booting off of a PXE-enabled mini-ITX mainboard (AMD Geode, VIA Graphics chipset) that I had lying around and it booted at 1280x1024 (or perhaps 1280x960, I'm not sure) without any config needed...   so I realize that this Wyse "Zero Client" is probably the source of the problems... but I just don't see why it shouldn't be possible to get it to boot at full resolution, given that it's apparently capable of it.

---

### Post by druhboruch on 2008-11-18
You have probably double checked that, but...
It may be simply a missing driver.
Not all drivers are under xserver-xorg-video-all.

Enter your chroot and apt-get install xserver-xorg-video-your_via_driver
Then delete xorg.conf from your chroot if it is created.
Don't forget to rebuild your image.

---

### Post by JGSD on 2008-11-19
> **druhboruch said:**
> 
Enter your chroot and apt-get install xserver-xorg-video-your_via_driver
Then delete xorg.conf from your chroot if it is created.
Don't forget to rebuild your image.

Unfortunately, xserver-xorg-video-via seems to have been removed in 8.10. However, all indications are that the xserver-xorg-video-openchrome should work for the Via P4M800 Pro and a apt-get install xserver-xorg-video-openchrome from the chroot says that this driver is already installed.

I am attaching the thin client's Xorg.7.log to this message. I am not very good at reading these things, although it seems pretty obvious that the openchrome driver isn't able to get much done. 

Can anyone give me any suggestions based on contents of the logfile?

---

### Post by druhboruch on 2008-11-19
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

You may have more success with this driver.
Good luck

---

### Post by JGSD on 2008-11-20
> **druhboruch said:**
> [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

You may have more success with this driver.
Good luck

Ok, thanks, I installed that driver in the chroot and it has definitely made an improvement. Now I am getting 1024x768 instead of 800x600.

Any tips for getting it up to 1280x1024, the monitor's native resolution? :-) I have tried putting in the following subsection under the "Screen" section and rebuilding the LTSP image, but it doesn't seem to have any effect:

```

SubSection "Display"
    Depth 32
    Modes "1280x1024"
EndSubSection

```

I also tried changing the depth to 16.

The Samsung 740B is listed as supporting 1280x1024 and the readme.txt that comes with the above VIA driver I just downloaded specifically states that this resolution is supported, so there's gotta be a way of getting it to work, right?

---

### Post by palitone on 2008-12-04
> **JGSD said:**
> Ok, thanks, I installed that driver in the chroot and it has definitely made an improvement. Now I am getting 1024x768 instead of 800x600.

Can you please show us the procedure in installing driver in the chroot. Thank you

---

### Post by Zurbriggen on 2008-12-05
I will like to know how you installed the driver also. And why do you deleted the xorg.conf from the chroot? How can you know that it is running properly?

Thanks a lot!

---


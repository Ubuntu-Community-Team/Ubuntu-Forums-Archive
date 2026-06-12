---
title: "USB external hard drive"
date: 2013-04-04
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-04-04
I have Ubuntu 12.10 installed on my internal HDD and daily 13.04 on my external usb hdd. Grub2 correctly identifies both installations, and bot run just fine after booting. When I choose the 13.04 entry after booting the internal hdd this message appears ```
HDIO_GET_IDENTITY failed
``` after 15 seconds or so the message dissappears and 13.04 boots just fine.
This slows the boot process - if I choose to boot to ```
usb storage device
``` directly the messages doesn't appear, but the boot process is just as slow.
I've searched on line and found plenty references to the message, but no solutions. I'd like to fix this.

Dell Inspiron 6000 Intel celeron 1.5Gz
2 Gb memory
```

/dev/sda:
 Timing cached reads:   746 MB in  2.00 seconds = 372.78 MB/sec
 Timing buffered disk reads: 104 MB in  3.01 seconds =  34.50 MB/sec
pfeiffep@de:~$ sudo hdparm -i /dev/sda


/dev/sda:


 Model=TOSHIBA MK4026GAX, FwRev=PA102D, SerialNo=75CI6825T
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=48
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=8
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78140160
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6


 * signifies the current active mode

```
```

pfeiffep@de:~$ sudo hdparm -tT /dev/sdb


/dev/sdb:
 Timing cached reads:   1018 MB in  2.00 seconds = 508.97 MB/sec
 Timing buffered disk reads:  80 MB in  3.03 seconds =  26.37 MB/sec
pfeiffep@de:~$ sudo hdparm -i /dev/sdb


/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 10 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_GET_IDENTITY failed: Invalid argument


```

Gparted correctly identifies the drive as SAMSUNG MP0402H.  

Any ideas about the HDIO .... message, and about the speed reported?

TIA
Pete

---

### Post by lisati on 2013-04-04
*Thread moved to **Ubuntu +1 (Raring Ringtail)**.*

---

### Post by grahammechanical on 2013-04-04
> [COLOR=#000000]When I choose the 13.04 entry after booting the internal hdd this message appears[/COLOR]

That statement is confusing me. If you are booting the internal hdd then you should be loading Ubuntu 12.10. So, how is it possible that you can choose to boot 13.04 after you boot into 12.10? I do not understand.

Where is the Grub menu? In the MBR of the internal hard disk? Or in the MBR of the external hdd? What speed setting is the USB device set for in the BIOS. There is a big difference between "High Speed" and "Full Speed."

By the way this is not 13.04 specific. [http://askubuntu.com/questions/103065/why-do-i-get-hdio-get-identity-failed-message-when-booting-with-external-usb-h](http://askubuntu.com/questions/103065/why-do-i-get-hdio-get-identity-failed-message-when-booting-with-external-usb-h)

[http://ubuntuforums.org/showthread.php?t=1867393](http://ubuntuforums.org/showthread.php?t=1867393)

My wild guess would be to examine the BIOS settings for the hard drives. You have have a setting that is prompting the BIOS to look for that Identity. 

Check this out

[https://bbs.archlinux.org/viewtopic.php?pid=1015693](https://bbs.archlinux.org/viewtopic.php?pid=1015693)

Regards.

---

### Post by pfeiffep on 2013-04-04
Thanks for your response.
> [COLOR=#000000]That statement is confusing me. If you are booting the internal hdd then you should be loading Ubuntu 12.10. So, how is it possible that you can choose to boot 13.04 after you boot into 12.10? I do not understand.[/COLOR]The internal hard drive has a grub2 menu ... grub2 utilizes os prober  ...  so when my usb hd is connected it finds the raring install

> [COLOR=#000000]Where is the Grub menu? In the MBR of the internal hard disk? Or in the MBR of the external hdd? What speed setting is the USB device set for in the BIOS. There is a big difference between "High Speed" and "Full Speed."[/COLOR] There is a grub2 menu installed on both the hard drives which enables me to transport the usb hd to any pc. This is usb2 not 3 so I don't believe those options are available.

> [COLOR=#000000]By the way this is not 13.04 specific. [/COLOR][http://askubuntu.com/questions/10306...external-usb-h]("http://askubuntu.com/questions/103065/why-do-i-get-hdio-get-identity-failed-message-when-booting-with-external-usb-h")I agree not 13.04 specific a forum moderator moved this post from hardware. Yes I'm a double dipper:popcorn:
> [COLOR=#000000]Check this out[/COLOR]
[https://bbs.archlinux.org/viewtopic.php?pid=1015693](https://bbs.archlinux.org/viewtopic.php?pid=1015693) I had read that plus quite a bit more - mostly indicating this is NOT serious ... it slows boot time however

---

### Post by kevpan815 on 2013-04-05
As far as I know Ubuntu does NOT officially Support Installing onto an External Hard Drive, although I actually have been Successful once or twice at doing so. And it was only due to the fact that I was using a Mac at the time that allowed me to do so. What I suggest for one thing is make sure that your BIOS and/or UEFI Firmware is Compatible with an External Installation. Just FYI.

---

### Post by cariboo on 2013-04-05
Why wouldn't Ubuntu be supported no matter how it's installed. The op has found a great solution to have basically a portable setup that can be moved from computer to computer.

As a side note threads concerning (or mentioning) 13.04  posted in other sections of the forum won't be moved here after about the 11th of April.

---

### Post by kevpan815 on 2013-04-05
Cariboo907, there are some OLD Apple FAQ's that say that installing on an External Drive is not supported at least for Apple Machines. If that is no longer true, than those outdated FAQ's in the Apple Sub-Forum should be Updated or Removed. :-)

---

### Post by pfeiffep on 2013-04-05
> [COLOR=#000000]cariboo907[/COLOR]
[COLOR=#000000][INDENT]**Re: USB external hard drive**
Why wouldn't Ubuntu be supported no matter how it's installed. The op has found a great solution to have basically a portable setup that can be moved from computer to computer.

As a side note threads concerning (or mentioning) 13.04 posted in other sections of the forum won't be moved here after about the 11th of April.[/INDENT]
[/COLOR]
Thanks for the kudo.:)
I fail to understand the side note ... I'm about 99% certain this has to do with hardware and not Ubuntu version - 1% maybe grub2:confused:

---

### Post by jerrylamos on 2013-04-05
> **kevpan815 said:**
> As far as I know Ubuntu does NOT officially Support Installing onto an External Hard Drive, although I actually have been Successful once or twice at doing so. And it was only due to the fact that I was using a Mac at the time that allowed me to do so. What I suggest for one thing is make sure that your BIOS and/or UEFI Firmware is Compatible with an External Installation. Just FYI.
?  I've been testing "unstable" U+1 development booting from USB external drive for years on netbook, notebook, tower.

Raring i386 and amd64 run just fine from in this case SSD on an external USB drive, to an Acer Aspire One netbook with 20" external 1600x900 monitor wireless keyboard and mouse.

Now USB booting on my 2005 Thinkpad is pretty shaky.  That notebook's bios support of USB is marginal.

Testing on USB drive helps (but not eliminates) early development screw ups where Grub2 fouls up and I have to do Grub Rescue or wipe the hard drive and start over.  This is development.....

Having said all that, on occasion U+1 ubuntu installs on the Acer 5253 notebook won't boot so I do a Grub Rescue O.K.  Most of the time.  Solid as a rock on the little netbook and the tower.

---

### Post by cariboo on 2013-04-05
> **kevpan815 said:**
> Cariboo907, there are some OLD Apple FAQ's that say that installing on an External Drive is not supported at least for Apple Machines. If that is no longer true, than those outdated FAQ's in the Apple Sub-Forum should be Updated or Removed. :-)

The only Apple hardware I use at the moment, is a way old G3 that runs Debian stable, and is used as an mp3 jukebox. If some of the faqs in the Apple sub-form are out of date, please report them, so that we can do something about them.

---

### Post by cariboo on 2013-04-05
> **pfeiffep said:**
> Thanks for the kudo.:)
I fail to understand the side note ... I'm about 99% certain this has to do with hardware and not Ubuntu version - 1% maybe grub2:confused:

Yes it is, but you mentioned 13.04 in the thread, and one of the mods automagically assumed that the thread actually had something to do with Raring, so it was moved here.

---

### Post by GeorgeVita on 2013-04-05
> **pfeiffep said:**
> I have Ubuntu 12.10 installed on my internal HDD and daily 13.04 on my external usb hdd. Grub2 correctly identifies both installations... 

> **jerrylamos said:**
> ... Testing on USB drive helps (but not eliminates) early development screw ups where Grub2 fouls up and I have to do Grub Rescue or wipe the hard drive and start over...

Many "old" BIOS identify an USB-HDD as USB-FDD choosing the lower throughput "Full Speed" mode. Also multi-partitioning is not covered in a Floppy! You can determine if you faced this problem from a GRUB prompt (press "[FONT=Courier New]**C**[/FONT]" at GRUB menu) using the command "[FONT=Courier New]**ls**[/FONT]". Your internal hard drive will be (HD0) and your partitions (HD0,x) or (HD0,MSDOSx). Your USB mass storage will be shown as (HD1) which means HDD or (FD0) if supposed to be a FDD.

Best setup for a "true portable system" is to attach your HDD using SATA into your desktop/laptop/netbook, do an "entire hard drive" installation using the first partition for the whole system (or the /boot directory) and then place the HDD into the USB>SATA enclosure.

---


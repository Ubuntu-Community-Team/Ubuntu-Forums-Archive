---
title: "xSeries 232 RAID problems"
date: 2010-02-25
forum: Server Platforms
---

### Post by lazychris2000 on 2010-02-25
I just picked up 2 IBM xSeries 232 servers at a local thrift store (you can imagine how excited I was to find these buried back in a pile of junk) and have been having problems getting ubuntu 9.10 server edition (actually, any server edition--I have tried all of them as far back as 6.06) installed so I can use it as a web/file server.  The installer gets to the partitioner, doesn't detect any drives and asks me to load SCSI drivers.  I select the ips driver, but it still does not detect any disks.  I am using a 64bit, 66MHz serveRAID 4lx card with 6x 18GB ST318452LC harddrives, configured as a 5-drive RAID5 array with 1 hotspare.  I have tried everything I could think of, including switching to tty2 and manually modprobing the ips module.  I noticed there was an option to load drivers from a USB drive, but I can't find any ubuntu drivers for the card.  
Other system Specs:
2x Pentium III 1.133 GHz
512MB (4x128MB) registered ecc PC133 (soon to be 4GB :D )
OnStream  30GB ADR tape drive
Rosewill PCI RC400-LX gigabit network card

I have read other people's suggestions about using the desktop version and stripping out the unnecessary packages, but I would much rather just install the server edition to begin with.  I am confident that once I get the RAID drivers, I won't have any issues getting it installed.

Attached are the lshw, lspci, and lsmod from the desktop version, which, strangely enough, loaded the scsi drivers and even let me partition the array.  Maybe these files will be helpful to someone, because apparently, they are not helpful to me.
Thanks in advance!

---

### Post by windependence on 2010-02-25
You need the IBM ServerRAID configuration disk. You can download it online for your version of the controller you have. You boot from that disk first and then configure your raid from that disk. After that you can load your OS whatever it might be. Many older servers are like this (Compaq).

-Tim

---

### Post by lazychris2000 on 2010-02-25
I already did that.  As I said in my post, it has been configured with 5 drives in raid5 with 1 hotspare.  Unless you are trying to tell me that I can load the drivers from the configuration disc?

---


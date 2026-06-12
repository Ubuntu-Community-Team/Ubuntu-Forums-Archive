---
title: "From WinServer to *ubuntu: Getting in to deep"
date: 2008-08-18
forum: Server Platforms
---

### Post by HackMaster on 2008-08-18
Here is what I am trying do: I recently got quite angry with my server and decided that it was not worth it to keep dealing with the crap of WinServer 2003 and decided to switch to a linux server. I have 2 other Ubuntu desktops and I feel confident, but I found a tutorial to help me out. { [http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) }

First, the hardware:
Dell Poweredge 2300
2x 500MHz PIII
2GB RAM (4x512MB)
DELL SCSI Backplate for:
3x 10000RPM SCSI 16GB
Random IDE PCI Card for:
2x misc IDE Hard Disks (Storage)
2x 100MBIT NICs
2MB GFX system, mouse, keyboard, dell proprietary admin port

The Goal:
The server should be able to handle:
-Routing/NAT
-DHCP
-Apache/PHP/MySQL
-Authenticated File Sharing with Win Clients (different permissions per user)
-Bittorrent
-Headless with optional GUI for intermittent administration
-And if possible a way to get CDs to be automatically ripped when inserted.


The tutorial suggested xubuntu to keep things light and still have a GUI to administer from when necessary. Unfortunately, I cannot get it to boot from the LiveCD. I am gonna install it to see if thats the issue but it is saying lots of errors that I attribute to the unusual hard drive issue.

```
209.{RANDOM NUMBERS} ata2.00: status: {DRDY ERR}
209.{RANDOM NUMBERS} ata2.00: error: {IDNF}
209.{RANDOM NUMBERS} ata2.00: exception Emask 0x0 SAct SErr 0x0 action 0x0
209.{RANDOM NUMBERS} ata2.00: BMDMA sat 0x5
209.{RANDOM NUMBERS} ata2.00: cmd c8/00:08:00:00:00/00:00:00:00/e0 tag 0 dma 4096

```

That entry is repeated over and over again with some of the numbers changed. Any help is appreciated!

---

### Post by cdenley on 2008-08-18
Try some different boot options.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
On the Dell's we use, Hardy gave me a similar problem until I added irqpoll to the boot options.

---

### Post by HackMaster on 2008-08-18
I just tried IRQPoll with no success. Is there much of a chance that if one of the options listed on the page will make the computer useless as a server? I think I want ACPI and that kind of thing.
The real issue is that I am not used to actual servers, just desktops acting like servers. It took me a good week to figure out the boot order of this thing, and the low-level stuff is way over my head.
I refuse to give up and I have set up a temporary replacement for the network management so I can take my time and do this right.

Any help is greatly appreciated. If you have a moment, IM and Twitter are all great options to speak with me in near-realtime if you want.
Thanks!

---

### Post by HackMaster on 2008-08-18
I just found this thread : [http://ubuntuforums.org/showthread.php?t=217667](http://ubuntuforums.org/showthread.php?t=217667)

I am currently researching some of what they were mentioning.
NOTE: I do not have RAID set up at all.

---

### Post by axcrit on 2008-08-18
my solution has actually been ubuntu 8.04 server alternative install since you can pick most of the options you want, dhcp, dns, smb, web, mysql and php.  

My server at home is a dell power edge sc1435:
Dual Core AMD Opteron 2.0 
2 GB
500 GB x2 hardware raid (mirror)
Gigabit nic x2
16meg intel video

So I loaded ubuntu server and only added the main lamp stuff cause I have a linksys RV082 Router/firewall/vpn server.  Then added xubuntu for a very low mem gui when needed.  Added vmware server and windows XP which runs utorrent, peer guardian and iTunes.  SMB shares are easy and permissions..  Once you get the basics up I'd load webmin.  You can take care of all the stuff from in there.  Also, it's a web interface so it fits in your headless operation wish.

---

### Post by HackMaster on 2008-08-19
Just wanted to follow up. I was finally able to get the LiveCD of Xubuntu to boot by using the noapic and irqpoll flags and setting the Dell "PERC 2/SC" Backplate to MASS STORAGE mode. Even then it took several tries.
After a long and error filled boot, however, all 5 HDs are detected and quite happy. And the icing on the cake? The dual NICs are also there and happy responding. I knew that the boot would be the difficult part of the equation but the simple solution is definatly a marked improvement over WinServer. It took much longer to get WinServer to boot.

Now off to other things while the hard disks repartition themselves!

---


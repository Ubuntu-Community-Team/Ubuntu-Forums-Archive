---
title: "Can't create a LiveCD to save my iso"
date: 2010-06-21
forum: System76 Support
---

### Post by watchpocket on 2010-06-21
Using first Brasero, then K3b, I burned (several times) the torrent "ubuntu-10.04-desktop-amd64.iso" to a TDK 700MB 80min CD-R with (a possibly unsupported) write speed of 4x (the only "supported" speed was 40x), then to a Memorex 700MB 80min CD-R using slowest supported write speed of 8x.  

Finished "successfully," in every case, but then got this trying to mount both CD-Rs:

[COLOR=Red]Unable to mount Ubuntu 10.04 LTS amd64

Error mounting: mount exited with exit code 32: [/COLOR] [COLOR=Red]
mount: block device /dev/sr0 is write-protected, mounting read-only 
mount: wrong fs type, bad option, bad superblock on /dev/sr0, missing codepage or helper program, or other error

In some cases useful info is found in syslog - try[/COLOR] [COLOR=Red]
       [COLOR=Blue]dmesg | tail[/COLOR]  or so

[COLOR=Blue]```
--> dmesg | tail  
[  490.420005] ata2: link is slow to respond, please be patient (ready=0)
[  520.080006] ata2: COMRESET failed (errno=-16)
[  520.080012] ata2: limiting SATA link speed to 1.5 Gbps
[  520.080014] ata2: hard resetting link
[  525.090005] ata2: COMRESET failed (errno=-16)
[  525.090010] ata2: reset failed, giving up
[  525.090012] ata2.00: disabled
[  525.090029] ata2: EH complete
[  525.090123] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 1651.852079] ath5k phy0: unsupported jumbo
```[/COLOR][COLOR=Black]So, how can I: 

(a)   un-write-protect device /dev/sr0 (if that in fact is the right thing to do);
(b)   make sure the right fs type is used;
(c)   make the bad option and bad superblock good; and
(d)   find the missing codepage or help program?[/COLOR]
[/COLOR]

---

### Post by thomasaaron on 2010-06-21
Re-download your image and try again. It sound like either the image or the burn is corrupted. But since the burn reports "Successful," then maybe the image is faulty.

---


---
title: "P2 hang after LAMP server install"
date: 2006-09-25
forum: Server Platforms
---

### Post by arava on 2006-09-25
Hello everyone:

This is the first time I have tried to install Ubuntu 6.06 LAMP and I am having problems on my target machine. Hopefully someone can point out what I'm doing wrong and how to fix it.

All the installs seems to go fine until the restart. When mySQL tries to start the machine hard hangs. The messages are not helpful. Installing the LVM with LILO displays more interesting messages. Again these are not logged in syslog but are similar to the ones below.

Using the desktop LiveCD works, but the HDD is not visible and syslog records many of the following messages:
```
Sep 25 04:13:59 ubuntu kernel: [   46.513268] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Sep 25 04:13:59 ubuntu kernel: [   46.513300] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Sep 25 04:13:59 ubuntu kernel: [   46.513320] ide: failed opcode was: unknown
Sep 25 04:13:59 ubuntu kernel: [   46.513337] end_request: I/O error, dev hdc, sector 1430336
Sep 25 04:13:59 ubuntu kernel: [   46.513358] Buffer I/O error on device hdc, logical block 178792
```

Some of the text displayed on screen when using LVM/LILO:
```
hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: status=0x84 {DriveStatusError BadCRC}
ide: failed opcode was: unknown
```
(full screen photo attached)

I'm using an Asus P2B motherboard.
I've tried another machine (similar motherboard) with the same results. So it is not the hardware.

I've tried installing the Ubuntu server disk on a P4 (Intel motherboard) and it does not have this problem.

I'm guessing that there is a problem with the IDE driver not working with something on this family of ASUS motherboards.

I was hoping to use Ubuntu as a LAMP server because I was impressed with the how good the desktop version looked and ran off the CD. Any help is appreciated.

---

### Post by arava on 2006-09-28
Hi:

Perhaps I've posted this to the wrong forum or I'm doing something else wrong. If so, would someone please advise me on where I should post this question.

I've tried installing Red Hat 9, Fedora Core 3 and FC5 on this machine. They do not exhibit the above problem; i.e. they work. Although I have struggled, I am not familiar with Linux enough to configure them properly.

Ubuntu looks like it has a better and easier setup. I think that it is a better system for me to learn on, but so far the latest release of Ubuntu doesn't work!

BTW, Windows works quite happily on these machines.

So, I would like the experts here to advise me on what I should do to get Ubuntu past the installation. It doesn't seem right to me that Ubuntu cannot work on an Asus motherboard.

---


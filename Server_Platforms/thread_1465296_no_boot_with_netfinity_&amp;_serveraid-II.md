---
title: "no boot with netfinity &amp; serveraid-II"
date: 2010-04-29
forum: Server Platforms
---

### Post by paulegc on 2010-04-29
Quite a tricky little problem here. I would be very grateful for that nugget of useful input to get things working.
 
Successfully installed Ubuntu server on an old IBM Netfinity 5500 with serveraid-II hardware raid card, but the boot sequence stops at an image requesting insertion of a bootable floppy and request to press F1.
 
Tried several different hardware RAID configurations, the latest one seemed moderately likely to boot, but needless to say it didn't.
 
I have found several threads around the web saying that grub doesn't cope well with hardware RAID and one thread suggested setting up a single disk in it's own array as RAID 0 and putting /boot on it. This is where we are now, not booting.
 
I tried to discover if I could turn off the RAID features of the card and use s/w RAID, but there's nothing on the Serveraid manager utility.
 
Then I wondered if I could build a floppy to take care of the initial stages of booting. Didn't get very far with that. I needed to 'modprobe floppy' and so on, but that failed - modprobe floppy could not load /lib/modules/2.6.31-14-generic/module.dep, no such file or directory.
 
Then I created a symbolic link to make .../2.6.31-14-generic-pae visible as ...generic. This time modprobe crashed with some other message, so I gave up on that.
 
What's my next best thing to try?
 
Thanks in anticipation.

---


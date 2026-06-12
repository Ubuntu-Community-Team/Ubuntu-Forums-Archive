---
title: "What happens if you have more than 26 disks?"
date: 2008-01-11
forum: Server Platforms
---

### Post by Cadmus on 2008-01-11
Ok, it may seem like a stupid question, but I'm looking at iSCSI and one question has popped up, for my own curiosity I was hoping someone might have the answer.

We all know HDs are named sda, sdb, sdc and so forth, but what happens in linux if you have more than 26 disks? What do the device names become?

---

### Post by insane_alien on 2008-01-12
double last letters perhaps? i have no idea. i only have 4 disks in my machine.

---

### Post by amo-ej1 on 2008-01-12
When you look at the kernel documentation there is a file called Documentation/devices.txt this one states which major number are allocated to which devices and how. So here you can conclude the following

major number 8 maps to /dev/sda till /dev/sdp 
major number 65 maps to /dev/sdq till /dev/sdaf
major number 66 maps to /dev/sdag till /dev/sdav
major number 67 maps to /dev/sdaw till /dev/sdbl 
<snip>
and it all ends at 
major number 135 maps to /dev/sdig till /dev/sdiv 

Meaning once you reach 256 scsi disks, THEN you will have a problem ;)   When someone provides me with 257 scsi disks i'll gladly give it a try ;)

---


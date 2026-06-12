---
title: "System Crash When Copying Large File"
date: 2010-06-15
forum: Server Platforms
---

### Post by TyIzaeL on 2010-06-15
Hello,

I am having a bit of a problem with my Ubuntu Server 10.04 install. I think it might be a kernel problem. Basically, what happens is when I copy a large file (a 160GB disk image) to my drive (>60GB) the system consistently crashes after about 60GB of the file is transferred. It doesn't matter if I am sending the file using cifs, or over SSH. Checking syslog ([paste dump here]("http://paste.ubuntu.com/450086/")), it seems these flush errors always appear shortly before the crash occurs.

The destination filesystem is a hardware RAID 10 array with 2TB of space. It is formatted as EXT4.

---

### Post by CharlesA on 2010-06-15
Can I suggest looking at the RAM?

I had a similar thing happen when I originally set my file server up - it would reboot whenever I copied a large amount of data. Turned out that it didn't like the memory, getting new RAM fixed the problem for me. :-)

---

### Post by TyIzaeL on 2010-06-15
I will run memtest on the system and report back.

---

### Post by TyIzaeL on 2010-06-16
> **CharlesA said:**
> Can I suggest looking at the RAM?

I had a similar thing happen when I originally set my file server up - it would reboot whenever I copied a large amount of data. Turned out that it didn't like the memory, getting new RAM fixed the problem for me. :-)
Memtest after three passes is showing no errors.

---

### Post by TyIzaeL on 2010-06-17
When I create the large file locally, there is no problem. The crash only occurs when I try to have the machine receive the file over the network.

---

### Post by BobVila on 2010-06-17
Ignore me. took a look at pastebin

---

### Post by Mighty_Joe on 2010-07-06
I may have the same problem: [see here]("http://ubuntuforums.org/showthread.php?t=1521238").

---

### Post by iponeverything on 2010-07-06
maybe this bug?:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577785](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577785)

---


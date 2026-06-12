---
title: "Ubuntu Server won't boot"
date: 2011-03-09
forum: Server Platforms
---

### Post by Nimbu on 2011-03-09
Hi

Im trying to set up a home server running ubuntu server 10.04 . I am using a dell optiplex GX240. 

Anyway, I installed ubuntu server ok. I had problems setting up the wireless card, so I followed this guide: [http://ubuntuforums.org/archive/index.php/t-476655.html](http://ubuntuforums.org/archive/index.php/t-476655.html) . After I restarted the networking daemon the computer froze. I had to hold in the power button to turn off the computer. Now when I try to attempt to start the server I get an error.

Please help me fix this problem.

P.S sorry for the large image

---

### Post by garfonzo on 2011-03-09
You'll get the message shown in that picture when you do a hard shutdown (which is what you did). My experience with this situation is that it will simply check the file system, and then carry on as usual. This disk check, however, can take a while. 

Have you left it to perform this check? Does it ever finish?

---

### Post by cariboo on 2011-03-09
I'd suggest booting from a live cd and running fsck on /dev/sda2

---

### Post by Nimbu on 2011-03-09
> **garfonzo said:**
> You'll get the message shown in that picture when you do a hard shutdown (which is what you did). My experience with this situation is that it will simply check the file system, and then carry on as usual. This disk check, however, can take a while. 

Have you left it to perform this check? Does it ever finish?

I have left it to run for 30 minutes. I have one 500gb drive with 3 partitions.
one swap partition 2gb, one os partition 50gb ext4 (i think this is sda2) and a 450gb partition ext2. Seeing as its only 50gb, I don't think it should take very long to complete a disk check. Any ideas to get it to boot fully.

---

### Post by Nimbu on 2011-03-09
> **cariboo907 said:**
> I'd suggest booting from a live cd and running fsck on /dev/sda2

I have tried to boot from a live cd but can't get any farther than the ubuntu logo.  Not sure whats going on. btw this computer was running windows xp without any trouble.

---

### Post by Nimbu on 2011-03-09
I have tried booting up the live cd for ubuntu desktop 9.10 . It wouldn't boot until I turned on the follwing settings:
acpi=off, noapic, nolapic, edd=on, nodmraid. I only managed to boot the live cd once using those settings but I couldn't get it to boot again. Very frustrating. What is the problem here?

---

### Post by Vegan on 2011-03-09
A lot of Dell machines use unorthodox gear so I avoid them like the plague.

I buy individual components and build machines that way. A lot easier and works like a charm.

I have an Acer machine and it like Ubuntu fine. It came with XP home but I dumped that and repurposed it as a server.

---

### Post by Nimbu on 2011-03-10
> **Vegan said:**
> A lot of Dell machines use unorthodox gear so I avoid them like the plague.

I buy individual components and build machines that way. A lot easier and works like a charm.

I have an Acer machine and it like Ubuntu fine. It came with XP home but I dumped that and repurposed it as a server.

Trying to make it work is taking too much time so I will unfortunately have to run Windows server 2003 :( . I will try to install ubuntu server on another machine in the future hopefully :D

---


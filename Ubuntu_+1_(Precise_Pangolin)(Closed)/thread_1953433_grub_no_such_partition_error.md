---
title: "grub no such partition error"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by spiky001 on 2012-04-06
Hi  I have been using 12.04 version for a few months and have always had a problem with booting after updates, Normally I can get the laptop to boot running the commands at grub prompt set root=(hd0,5) linux /boot/vmlinuz what ever the kernel is.  This time I have got No such partition, Any commands I use like ls or use the TAB key to auto fill wont work  grub> set root=(hd0,5) grub>ls  returns no such partition any ideas how to resolve

---

### Post by raja.genupula on 2012-04-06
have you tried boot repair ? 

if that wont help , then post output of bootinfoscript . 

all the best , :)

---

### Post by cyprys on 2012-04-06
Same problem here after upgrade 11.10 to 12.04 yesterday.
What's worst, I have no other internet access capable machine (writing from work and it's last day before holidays... bummer, huh?). Will try boot-repair from liveUSB, thanks.

---

### Post by dino99 on 2012-04-06
follow this grub2 link below

---

### Post by oldos2er on 2012-04-06
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by cyprys on 2012-04-06
It doesn't help at all.

> If at the grub prompt, type ls and ENTER. If the command does not display all the partitions, reboot and enter your computer's BIOS setup. Ensure the BIOS reports the full disk size. If it doesn't, check for LBA/partition settings or obtain a BIOS update from the manufacturer.

I use top shelf hardware, nothing older than several months, a year at most. Besides, it used to work well with 11.10. No LBA problem then, not now.

> grub> ls
error: no such partition
grub>

My boot is on /dev/sda1 and it's first on the drive phisically (double checked in Disk Utility). Is the following correct?
> root=(hd0,msdos1)
prefix=(hd0,msdos1)/grub


[edited]
I gave up on tinkering myself and used boot repair. Recommended fix (one click solution) solved the booting issue. Here's the catch: while installing 12.04 my sda drive mysteriously became sdb, therefore no root value I set manually could work. Also I could only log in as a guest, because my /home was inaccessible (it used to be on separate partition) - pressing 'M' from manual recovery mode and putting into console "mount /dev/sdb2 /home" solved the issue (if you have the same problem substitute sdb2 with correct device). Afterwards I still couldn't log in due to lack of permissions on my old $HOME and chown or chmod didn't actually help, however creating a new user and copying all user folders was an acceptable workaround. Hope I helped someone.

---

### Post by rsisto on 2012-04-12
Wow, I had this problem when updating ubuntu 11.10 to 12.04... I think the best is to reinstall ubuntu again, I have previously installed 11.10 less than a month ago.

It gets really frustrating... I was trying to solve another issue when updating, but something else breaks, it seems it's the most common behavior with ubuntu so far...

Perhaps I'll try to repair grub first, but it seems ridiculous to fix something that's nearly fresh installed! A fresh install seems to be the most obvious way. 

I'll let you know what I decide tomorrow :P

---


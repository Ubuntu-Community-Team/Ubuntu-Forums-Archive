---
title: "Software RAID: no devices found for /dev/md0"
date: 2005-11-12
forum: Server Platforms
---

### Post by ram1 on 2005-11-12
I have tried to setup a software raid0 array. It consists of two identical SATA disks (/dev/sda, /dev/sdb). I have created one partition on each drive with the RAID autodetect type.

I also used mdadm --create /dev/md0 --level 0 --raid-devices=2 /dev/sda1 /dev/sdb1

I also created a reiserfs filesystem on that partiton: mkreiserfs /dev/md0

all this works just fine.

However, the problem is when I reboot the server.
When in single-user mode and mdadm-raid runs I get the error message:
mdadm: no devices found for /dev/md0 [fail]

To make the raid working, I have to manually assemble the array or run mdadm-raid during startup in rc2. Since Im planing to use this raid0 as /home, I want to mount it in fstab (which is done in single-user mode)

Any ideas why this aint working in single-user mode?

---

### Post by LordHunter317 on 2005-11-12
First off, RAID-0 is a dangerous bad idea, especially for /home.  Just say no.

And I'm confused?  It doesn't work if you boot single-user (i.e., runlevel 1) and then works fine at runlevel 2, or doesn't work at all at runlevel 2?

---

### Post by ram1 on 2005-11-12
works in runlevel 2, not in runlevel 1

---

### Post by LordHunter317 on 2005-11-12
Ok, that's only a minor PITA really, as you shouldn't normally be in runlevel 1.  What errors does mdadm log (to /var/log/messages or wherever it does)  Anything else?

---

### Post by ram1 on 2005-11-12
I dont seemt to get any error messages in /var/log/messages.

Just as a clarification:
mdadm wont start the raid array if the script is executed in runlevel 1, it just says: mdadm: no devices found for /dev/md0

when executing the script in runlevel 2, it starts without any problems and can be mounted right away.

---

### Post by LordHunter317 on 2005-11-12
Post the output of ls /etc/rc1.d/ and /etc/rc2.d/ please.

---

### Post by ram1 on 2005-11-12
I found it out myself, the problem was simply that my sata controller got  initialized after the mdadm-raid tried to setup the raid array. I just rearranged some links in rcS.d. The sata controller didnt draw much attention to itself so I didnt notice at a first glance. My bad.

Thank you for your helpfullness LordHunter.

---

### Post by LordHunter317 on 2005-11-12
Yes, that wold cause it to happen.  Odd it was happening only under rc1 and not rc2 though, that likely it implies it was a race issue.

Adding the module to /etc/modules may prevent it from happening in the future, FWIW.

---

### Post by poptones on 2005-11-12
Man, you liberals... always playing the race card...

---

### Post by LordHunter317 on 2005-11-12
Was that serious or a joke?  The behavior is very indicitive of a race condition.

---

### Post by grendelkhan on 2005-11-14
It's a joke, and a darn funny one at that. :)

---


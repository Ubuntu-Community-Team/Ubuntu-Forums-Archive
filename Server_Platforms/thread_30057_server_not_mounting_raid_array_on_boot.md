---
title: "server not mounting raid array on boot"
date: 2005-04-27
forum: Server Platforms
---

### Post by ryness on 2005-04-27
i have five 160gb sata disks on an intel srcs16 raid controller, raid5 partitioned ext3 as sda1. when the server boots up it doesn't mount the array, altho it mounts the other ide disks in the system, even though the entry is in /etc/fstab. once the machine is loaded, i can "mount -a" and it mounts the  array. not sure if there's something weird with the raid card or if i config'd it wrong - any ideas?

/dev/sda1  /store  ext3  user,suid,dev,exec  0  0

---

### Post by mad_logic on 2005-04-27
Dude it seems like you've got more of an idea than I've got cause I'm using a Dell PowerEdge2800 I can't even install the OS (Hoary Kubuntu) because it says It can't detect any hard disks, and what puzzles me more is the fact that it doesn't even ask me for loading the drivers or anything...I actually gave up on it 'cause I was running out of time...

But I think you might have helped me, because I never tried installing one hard disk on the ide. Thanx mate, and sorry but I can't help you.

---

### Post by adeh on 2005-04-27
hafve you tried playing with the <options> section? Try "defaults".

Sorry, that's the only thing I can think of.

---

### Post by ryness on 2005-04-27
[QUOTE=adeh]hafve you tried playing with the <options> section? Try "defaults".

Sorry, that's the only thing I can think of.[/QUOTE]

<options> section of what?

---


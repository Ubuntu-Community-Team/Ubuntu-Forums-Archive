---
title: "Truecrypt and fsck"
date: 2006-11-15
forum: Server Platforms
---

### Post by ranpha on 2006-11-15
I'm almost finished testing encryption on my systems but before i switch my 2 terbyte databse over to a encryption (btw that including backups) i want tofind out if it's possible to do the same file check as a normal unencrypted file system. I tried it but i get a message

fsck.ext2: Device or resource busy tijdens openen van /dev/sdb1

Which is true because truecrypt has it mapped (not mounted yet)?

Is there a way to check your file system with a Truecrypt encryption on it?

---

### Post by ranpha on 2006-11-15
Never mind found it out

just 
 sudo fsck /dev/mapper/truecrypt0

and voila

oh and don't mount off course ust map

---


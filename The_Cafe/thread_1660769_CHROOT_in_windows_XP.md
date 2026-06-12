---
title: "CHROOT in windows XP?"
date: 2011-01-05
forum: The Cafe
---

### Post by kevin11951 on 2011-01-05
Does anyone know if its possible to chroot into an external hdd with Windows XP installed on it?

Basically, I need to install an application onto Windows XP SP3 for a client without booting the Windows install itself.

---

### Post by psusi on 2011-01-05
Umm... no.  If you want to install windows software into windows, you have to actually boot windows.

---

### Post by Chronon on 2011-01-05
No, chroot doesn't work like that.  You are running it from Linux.  You can't simply change root to some HD that doesn't contain a compatible system.

---

### Post by RiceMonster on 2011-01-05
You CAN mount the NTFS drive and copy files onto the drive, but you cannot run a windows installer from Linux.

I don't understand why you want to install without booting into Windows in the first place.

---

### Post by kevin11951 on 2011-01-05
Wait, when I say chroot, I just mean the Windows equivalent...

I work for a local high school, and they have a Windows XP image that self sets up during boot.  I have to install some stuff into the image w/o booting the image.

---

### Post by psusi on 2011-01-05
There is no windows equivalent, and if there were, you would still have to boot windows to do it.

---

### Post by Austin25 on 2011-01-05
Can you change the install directory in the installer?

---


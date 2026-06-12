---
title: "How To secure external HDD"
date: 2009-08-26
forum: Security
---

### Post by Ceiber Boy on 2009-08-26
hi  

this question has probability been asked a million times, but here it goes again.

i have an external HDD that i want to secure the data on, by encryption and not allowing others to access the drive.

i can use trucrypt to incrypt the data but the encrypted data files can still be deleated. which is what i'm trying to prevent.

dose anyone have any thoughts or idears from how to stop this from happening?

thnaks

---

### Post by Agent ME on 2009-08-27
Physical access is everything. If they have physical access to the harddrive, then there is nothing stopping them from deleting data on it, overwriting it with 0's, or putting a magnet to it.

However if you only ever have the harddrive connected to your computer and want to protect it from other users of your computer, you can set the permissions of it so only you can access the harddrive. I think you'd have to do some messing around in /etc/fstab, but not too sure. *(This obviously doesn't stop them from removing the harddrive, and plugging it into a different computer that doesn't have these permission settings.)*

---

### Post by bodhi.zazen on 2009-08-27
Permissions should be your first line of defense, but if the data is "sensitive" encryption is the best you can do.

As Agent ME indicated, if one has physical access they can delete, reformat, or destroy the drive.

---

### Post by snakeman21 on 2009-08-27
ABSOLUTE BEST SECURITY FOR AN EXTERNAL DRIVE:

Physically lock it up.

---

### Post by cariboo on 2009-08-27
+1, disconnect the cables and lock it away in a drawer when you aren't personally using the computer.

---

### Post by HermanAB on 2009-08-28
Here you go:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)
[http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf](http://www.aeronetworks.ca/LUKS-Mount-FreeOTFE.pdf)

If the whole file system is encrypted, then you need to enter a password in order to mount the drive.  So other users cannot see any files.  However, they can still go and format the whole thing...

---


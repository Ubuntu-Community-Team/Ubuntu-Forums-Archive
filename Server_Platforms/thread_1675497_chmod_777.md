---
title: "chmod 777 /"
date: 2011-01-25
forum: Server Platforms
---

### Post by pehden on 2011-01-25
Some how I wasnt looking at my script when i was editing it and chmod -R 777 /
my system, I have now seem to have it running again by the sudo /usr/bin/sudo and chmoding the sudoers and sudoers.d files but for some reason im not able to remove anything via apt-get or aptitude

one error apt-listchanges not found, and I get sevral errors for time outs and not found when apt-get upgrade or update.


Is there any cd or script that can run automated and correct all the file permissions.

---

### Post by HermanAB on 2011-01-25
Yup, there sure is one.  The Install script.

Backup your data and enjoy your nice newly installed system.

---

### Post by kevinthecomputerguy on 2011-01-25
I agree with HermanAB.
Backup your stuff, Grab your CD, and start over.

---

### Post by pehden on 2011-01-25
I think some one should make a script to fix this i can think of a way to do this in php put handling the errors would be tough for php to do.

---

### Post by pehden on 2011-01-25
For the reinstall can you reinstall the server without formating the drive? I dont have the time to wait for the server to move everything from /var to an alt location.

---

### Post by arrrghhh on 2011-01-25
> **pehden said:**
> For the reinstall can you reinstall the server without formating the drive? I dont have the time to wait for the server to move everything from /var to an alt location.

You can, but you still need to backup all your data... You should be backing it up anyways honestly.

---

### Post by matt_symes on 2011-01-25
Hi

> For the reinstall can you reinstall the server without formating the drive? I dont have the time to wait for the server to move everything from /var to an alt location.

That does also assume that everything you may have installed since install will also be happy with 777 permissions. This may or may not be the case. Also don't forget about updates.

[SIZE="3"]Backup, Backup,[/SIZE] [SIZE="2"]Backup, Back up,[/SIZE][SIZE="1"]Backup, backup.....[/SIZE]

Kind regards

---

### Post by wojox on 2011-01-25
> **pehden said:**
> I think some one should make a script to fix this

How about you just don't chmod -R 777 / anytime soon.

---

### Post by matt_symes on 2011-01-25
Hi

At least it wasn't chown.

Kind regards

---


---
title: "Can't install Ubuntu Server?"
date: 2013-06-23
forum: Server Platforms
---

### Post by TheMophead on 2013-06-23
I'm attempting to install Ubuntu Server 12.04.2 LTS on an old PC that I managed to piece together from old parts. I burnt the .iso like I've done hundreds of times for my other servers but when I boot the CD and get to the first screen, my keyboard locks up and I can't hit enter to proceed.

[Image]("http://mophead.eu/Images/IMAG0075.jpg")

Spec:

AMD Athlon XP 3200+
ASrock K7VT4A PRO
1.5GB's of RAM
1 80GB Samsung IDE HDD

---

### Post by CharlesA on 2013-06-23
Did you verify the md5sum/sha1sum of the ISO before burning it?

Are you using a USB or PS/2 keyboard?

---

### Post by MG2R on 2013-06-23
> **CharlesA said:**
> Are you using a USB or PS/2 keyboard?

This.

If you have an old motherboard (and thus an old BIOS), it might be so that the BIOS does not support USB keyboards natively.

---

### Post by TheMophead on 2013-06-23
> **CharlesA said:**
> Did you verify the md5sum/sha1sum of the ISO before burning it?

Are you using a USB or PS/2 keyboard?

I've verified the ISO and I'm confident that it works since I recently used it to update the OS on my DL380 G3 Server. I'm using a USB keyboard and I've tried a PS/2 Keyboard and I had no luck. I've even used a thumb drive but I was presented with this error:
> **[SIZE=3][No DEFAULT or UI configuration directive found!]("http://askubuntu.com/questions/30374/boot-failure-no-default-or-ui-configuration-directive-found")[/SIZE]**



---

### Post by CharlesA on 2013-06-23
Try a livecd first and make sure you can boot off it and everything works ok.

Then try installing the server version.

---

### Post by Treekodar on 2013-06-25
If it still isn't fixed by now, you could try and kickstart the installation to fill in the steps automatically. That should help with keyboard issues during installation at least. Alternatively, install via SSH.

---


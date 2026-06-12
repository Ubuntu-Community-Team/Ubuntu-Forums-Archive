---
title: "mount nero cd images"
date: 2014-04-27
forum: Server Platforms
---

### Post by Vegan on 2014-04-27
I was wondering do I need anything extra to be able to use cd images make from nero burning rom?

I was wanting to mount obviously as a CD and also to mount automatically, as it would be for a cd-rom server

---

### Post by nerdtron on 2014-04-27
Have you tried the following command:
sudo mount -o loop /path/to/iso/file /mount/point

If that works then you should you can try mounting it using the fstab:
/path/to/iso/file  /mount/point  udf,iso9660  user,noauto,exec,utf8  0  0

More explanation here [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Vegan on 2014-04-27
any real limit to the number of cd images i can present? I was aspiring to maybe have 20 or 30 optical images via SAMBA most likely

---

### Post by nerdtron on 2014-04-27
I don't think there's a limit as long as the server can handle the load. They are just basically local folder that the SAMBA users will access.

---

### Post by Vegan on 2014-04-27
some images are subscription based and expire eventually, so I guess I should use a database to keep track of those types

---

### Post by Vegan on 2014-04-28
the images are not all ISO as some are NRG which is the lower level image

---

### Post by nerdtron on 2014-04-29
Isn't NRG only for Nero software? Is it possible to convert them to ISO?
Another workaround would be to just copy those files by mounting them on windows, then copy the files to the ubuntu server and create samba shares for them. Is it possible?

---

### Post by Vegan on 2014-04-29
I have to use 3rd party software as Windows also will not mount them natively.

The popular Daemon tools can mount NRG images and then these can be shared, but I was hoping open source had figured it out

Daemon is limited in the number of images it can show before they want $

---

### Post by nerdtron on 2014-04-29
Have you seenthis post? [http://ubuntuforums.org/showthread.php?t=1829070](http://ubuntuforums.org/showthread.php?t=1829070)
You can either convert them to iso or mount them natively. Haven't tried it myself but it is worth a try.

Or if you have a gui, you can use FuriusISO or acetoneiso to mount them. Just install the program from the repository.

---

### Post by Vegan on 2014-04-29
That will not work with some DRMed images

---

### Post by Vegan on 2014-04-29
I have noticed CDemu but I have not sure if Ubuntu is using that, I am using the server variant, no GUI

---


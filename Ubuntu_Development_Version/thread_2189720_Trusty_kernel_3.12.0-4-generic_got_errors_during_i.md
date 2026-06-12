---
title: "Trusty kernel 3.12.0-4-generic got errors during installation"
date: 2013-11-23
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-11-23
I got kernel 3.12.0-4-generic in an update today and it got some errors that I can't remember off hand. But now everything looks weird.
All the icons are just red x's and the cairo dock icons are blue question marks. Even though I had only 2 kernels installed it was telling me to apt-get autoremove the 3.12.0-3-generic files.

I even tried **sudo apt-get purge linux-headers-3.12.0-3 linux-headers-3.12.0-3-generic linux-image-3.12.0-3-generic linux-image-extra-3.12.0-3-generic** and then 
**sudo apt-get install linux-headers-3.12.0-3 linux-headers-3.12.0-3-generic linux-image-3.12.0-3-generic linux-image-extra-3.12.0-3-generic**.
That seemed to go well so I purged and then readded the 3.12.0-4-generic kernel and got the same errors.
Of course I had to install linux-generic linux-headers-generic linux-image-generic along with the 4 3.12.0-4-generic files. But, my background is just a solid blue and the icons are all messed up.

Any one else have this issue?

PS. Ironically the cube still rotates. :) I've been in Flashback the whole time.

---

### Post by mc4man on 2013-11-23
There was a [known error with 3.8 - 3.9]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1253498") so maybe that was also trying to upgrade at same time as 4.10 (3.12.0-4-generic #10
In any event 4.10 is fine here & 3.8 can be removed

---

### Post by pqwoerituytrueiwoq on 2013-11-23
when i did my updates today  on my virtual machiene the 3.12.0-3 gave a error and the 3.12.0-4 worked fine i removed the old kernels (recover disk space) and the 3.12.0-4 kernel booted fine

---

### Post by Cavsfan on 2013-11-24
I booted into the 3.12.0-3 kernel and the same thing. 
So I purged and re-installed it and this is the error that it was getting.

```
Setting up linux-image-extra-3.12.0-3-generic (3.12.0-3.9) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.12.0-3-generic
) points to /boot/initrd.img-3.12.0-3-generic
 (/boot/initrd.img-3.12.0-3-generic) -- [COLOR=#ff0000]doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-3-generic.postinst line 491.[/COLOR]
vmlinuz(/boot/vmlinuz-3.12.0-3-generic
) points to /boot/vmlinuz-3.12.0-3-generic
 (/boot/vmlinuz-3.12.0-3-generic) -- [COLOR=#ff0000]doing nothing at /var/lib/dpkg/info/linux-image-extra-3.12.0-3-generic.postinst line 491.[/COLOR]
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
update-initramfs: Generating /boot/initrd.img-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.12.0-3-generic /boot/vmlinuz-3.12.0-3-generic

```

Going to try a reboot. :)

---

### Post by anca-emanuel on 2013-11-24
I got the same problem with icons.
I reinstalled ubuntu 14.04 and after sudo apt-get upgrade, got the same error message. This time I got to work,
sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache

after searching the internet, chmod the file, installing some package, the command above finally worked.

---

### Post by philinux on 2013-11-24
Same with 3.12.0-3 and 3.12.0-4 purged both for now.

---

### Post by Cavsfan on 2013-11-24
I gave up and had to perforn a clean install to fix it. I got an ISO that was created at 7 something this morning.  it came with 3.12.0-4-generic kernel installed and I installed Nvidia driver 331.20.

The extra repository was already commented out which was sweet but I still had to enable partners. I'm in Gnome Flashback with effects, compiz and got the cube rotating. So, for now everything is looking pretty sweet.
After installation there was just one file in the updates.

---

### Post by philinux on 2013-11-24
I can forsee a zsync and clean install tomoz.  ;)

---

### Post by Cavsfan on 2013-11-24
> **philinux said:**
> I can forsee a zsync and clean install tomoz.  ;)

Lol! :) It will be a lot better! Suspend worked from the gnome applet-indicator-complete but, I think it did before. Haven't tried anything else there yet.  :guitar:

---

### Post by Cavsfan on 2013-11-24
Back to cooking with gas. For now at least. :)

[[IMG]http://en.zimagez.com/miniature/screenshot1306.png[/IMG]]("http://en.zimagez.com/zimage/screenshot1306.php")

---


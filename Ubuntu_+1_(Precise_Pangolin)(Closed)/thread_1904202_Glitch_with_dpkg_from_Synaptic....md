---
title: "Glitch with dpkg from Synaptic..."
date: 2012-01-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2012-01-04
```
Selecting previously unselected package linux-image-3.2.0-7-realtime.
(Reading database ... 246348 files and directories currently installed.)
Unpacking linux-image-3.2.0-7-realtime (from .../linux-image-3.2.0-7-realtime_3.2.0-7.13~ppa1_amd64.deb) ...
[COLOR="Red"]debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog[/COLOR]
Done.
Selecting previously unselected package linux-image-realtime.
Unpacking linux-image-realtime (from .../linux-image-realtime_3.2.0.7.7~ppa1_amd64.deb) ...
Setting up linux-image-3.2.0-7-realtime (3.2.0-7.13~ppa1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-7-realtime /boot/vmlinuz-3.2.0-7-realtime
update-initramfs: Generating /boot/initrd.img-3.2.0-7-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-7-realtime /boot/vmlinuz-3.2.0-7-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-7-realtime /boot/vmlinuz-3.2.0-7-realtime
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-7-realtime /boot/vmlinuz-3.2.0-7-realtime
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-999-generic
Found initrd image: /boot/initrd.img-3.2.0-999-generic
Found linux image: /boot/vmlinuz-3.2.0-996-generic
Found initrd image: /boot/initrd.img-3.2.0-996-generic
Found linux image: /boot/vmlinuz-3.2.0-7-realtime
Found initrd image: /boot/initrd.img-3.2.0-7-realtime
Found linux image: /boot/vmlinuz-3.2.0-7-generic
Found initrd image: /boot/initrd.img-3.2.0-7-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
Setting up linux-image-realtime (3.2.0.7.7~ppa1) ..
```Yes, libgtk2-perl is installed...
I must admit I'm using X 1.12... and some other stuff...

---

### Post by Harry33 on 2012-01-04
I have been getting that same message for a long time now.
But, then again, I do not have libgtk2-perl installed. Just do not need it.

Anyways, that message is completely harmless.

---

### Post by zika on 2012-01-04
> **Harry33 said:**
> Anyways, that message is completely harmless.I know... ;)

---


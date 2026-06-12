---
title: "collision of kernel parts... / Launchpad bug 1118071"
date: 2013-02-07
forum: Ubuntu Development Version
---

### Post by zika on 2013-02-07
```
...Unpacking replacement libxi6:amd64 ...
Preparing to replace linux-image-3.8.0-4-generic 3.8.0-4.8 (using .../linux-image-3.8.0-4-generic_3.8.0-4.9_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.8.0-4-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-4-generic_3.8.0-4.9_amd64.deb (--unpack):
 trying to overwrite '/lib/modules/3.8.0-4-generic/kernel/drivers/ata/ahci_platform.ko', which is also in package linux-image-extra-3.8.0-4-generic 3.8.0-4.8
Examining /etc/kernel/postrm.d .
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic...
...
...Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-4-generic_3.8.0-4.9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Next attempt was successful:
```
Get:1 http://archive.ubuntu.com/ubuntu/ raring/main linux-image-3.8.0-4-generic amd64 3.8.0-4.9 [12.4 MB]
Fetched 12.4 MB in 6s (1,873 kB/s)                                             
(Reading database ... 313902 files and directories currently installed.)
Preparing to replace linux-image-3.8.0-4-generic 3.8.0-4.8 (using .../linux-image-3.8.0-4-generic_3.8.0-4.9_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.8.0-4-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
Setting up linux-image-3.8.0-4-generic (3.8.0-4.9) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-4-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-4-generic /boot/vmlinuz-3.8.0-4-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-030800rc6-generic
Found initrd image: /boot/initrd.img-3.8.0-030800rc6-generic
Found linux image: /boot/vmlinuz-3.8.0-999-generic
Found initrd image: /boot/initrd.img-3.8.0-999-generic
Found linux image: /boot/vmlinuz-3.8.0-996-generic
Found initrd image: /boot/initrd.img-3.8.0-996-generic
Found linux image: /boot/vmlinuz-3.8.0-4-generic
Found initrd image: /boot/initrd.img-3.8.0-4-generic
Found linux image: /boot/vmlinuz-3.8.0-0-lowlatency
Found initrd image: /boot/initrd.img-3.8.0-0-lowlatency
Found linux image: /boot/vmlinuz-3.7.0-6.dmz.1-liquorix-amd64
Found initrd image: /boot/initrd.img-3.7.0-6.dmz.1-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.bin
done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

---

### Post by dino99 on 2013-02-07
you're lucky  :D

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1118071](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1118071)

---

### Post by zika on 2013-02-07
> **dino99 said:**
> you're lucky  :D

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1118071](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1118071)
No, just persistent, relentless... ;)

---

### Post by zika on 2013-02-07
Error is occuring with other kernels also...
```
Unpacking replacement linux-image-3.8.0-999-generic ...
dpkg: error processing /tmp/linux-image-3.8.0-999-generic_3.8.0-999.201302070524_amd64.deb (--install):
 trying to overwrite '/lib/modules/3.8.0-999-generic/kernel/drivers/ata/ahci_platform.ko', which is also in package linux-image-extra-3.8.0-999-generic 3.8.0-999.201302060409
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
...
Errors were encountered while processing:
 /tmp/linux-image-3.8.0-999-generic_3.8.0-999.201302070524_amd64.deb

``````
:~$ sudo dpkg -i /tmp/linux-image-3.8.0-999-generic_3.8.0-999.201302070524_amd64.deb 
(Reading database ... 313903 files and directories currently installed.)
Preparing to replace linux-image-3.8.0-999-generic 3.8.0-999.201302060409 (using .../linux-image-3.8.0-999-generic_3.8.0-999.201302070524_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.8.0-999-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
Setting up linux-image-3.8.0-999-generic (3.8.0-999.201302070524) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-999-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-999-generic /boot/vmlinuz-3.8.0-999-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-030800rc6-generic
Found initrd image: /boot/initrd.img-3.8.0-030800rc6-generic
Found linux image: /boot/vmlinuz-3.8.0-999-generic
Found initrd image: /boot/initrd.img-3.8.0-999-generic
Found linux image: /boot/vmlinuz-3.8.0-996-generic
Found initrd image: /boot/initrd.img-3.8.0-996-generic
Found linux image: /boot/vmlinuz-3.8.0-4-generic
Found initrd image: /boot/initrd.img-3.8.0-4-generic
Found linux image: /boot/vmlinuz-3.8.0-0-lowlatency
Found initrd image: /boot/initrd.img-3.8.0-0-lowlatency
Found linux image: /boot/vmlinuz-3.7.0-6.dmz.1-liquorix-amd64
Found initrd image: /boot/initrd.img-3.7.0-6.dmz.1-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.bin
done
```Something is broken in ordering upgrades kernel-wise...

---

### Post by screaminj3sus on 2013-02-07
I think I had the same problem updating today via update-manager. It told me some packages failed to install, and then for some reason startup-disk creator opened with "ubuntu core installer". I ran update-manager again and it worked fine.

---

### Post by dino99 on 2013-02-07
This happen only the first time while upgrading; Refreshing the cache / updating again, make upgrading possible.

note: the issue is known, have been reported and already have many dupes; so stop the flood please.

---

### Post by zika on 2013-02-07
> **dino99 said:**
> This happen only the first time while upgrading; Refreshing the cache / updating again, make upgrading possible.

note: the issue is known, have been reported and already have many dupes; so stop the flood please.I'm sorry for any  flood You've seen... It will not happen again...
(I just thought that it would be useful to know that it does not depend on kernel being upgraded but the bug is elsewhere... It is happening in two very different ways of install/upgrade processes...)
 Mea culpa... Over&Out

---

### Post by kansasnoob on 2013-02-07
> **screaminj3sus said:**
> I think I had the same problem updating today via update-manager. It told me some packages failed to install, and then for some reason startup-disk creator opened with "ubuntu core installer". I ran update-manager again and it worked fine.

+1!

I was using Synaptic but the results were identical.

---

### Post by Harry33 on 2013-02-08
Yes the new 3.8.0-5.10 kernel fixes this issue.

linux (3.8.0-5.10) raring; urgency=low    [Tim Gardner]  * Release Tracking Bug     - LP: #1118568    * Bump ABI to fix install issue with 3.8.0-4.8.     Moving drivers/ata/*ahci* to linux-image caused an     install conflict with linux-image-extras without an     ABI bump.

---

### Post by abhis3k on 2013-02-08
> **Harry33 said:**
> Yes the new 3.8.0-5.10 kernel fixes this issue.

linux (3.8.0-5.10) raring; urgency=low    [Tim Gardner]  * Release Tracking Bug     - LP: #1118568    * Bump ABI to fix install issue with 3.8.0-4.8.     Moving drivers/ata/*ahci* to linux-image caused an     install conflict with linux-image-extras without an     ABI bump.

I can confirm this too. This is now fixed.

---

### Post by zika on 2013-02-08
If I may say, as OP, without making a &#8222;flood&#8220;, it is fixed even at my place...

---


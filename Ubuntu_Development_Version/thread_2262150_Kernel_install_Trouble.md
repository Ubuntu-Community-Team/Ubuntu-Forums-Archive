---
title: "Kernel install: Trouble"
date: 2015-01-23
forum: Ubuntu Development Version
---

### Post by zika on 2015-01-23
On this particular machine kernel was successfully installed (999) this very morning. Now it behaves like this when attempting to install any kernel:```
:/tmp$ sudo dpkg -i *.debSelecting previously unselected package linux-headers-3.19.0-031900rc5.
(Reading database ... 221952 files and directories currently installed.)
Preparing to unpack linux-headers-3.19.0-031900rc5_3.19.0-031900rc5.201501180935_all.deb ...
Unpacking linux-headers-3.19.0-031900rc5 (3.19.0-031900rc5.201501180935) ...
Selecting previously unselected package linux-headers-3.19.0-031900rc5-generic.
Preparing to unpack linux-headers-3.19.0-031900rc5-generic_3.19.0-031900rc5.201501180935_amd64.deb ...
Unpacking linux-headers-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Selecting previously unselected package linux-image-3.19.0-031900rc5-generic.
Preparing to unpack linux-image-3.19.0-031900rc5-generic_3.19.0-031900rc5.201501180935_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Setting up linux-headers-3.19.0-031900rc5 (3.19.0-031900rc5.201501180935) ...
Setting up linux-headers-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Setting up linux-image-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
```No initramfs hook called.
Also```
:/tmp$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-031900rc5-generic
Found linux image: /boot/vmlinuz-3.19.0-999-generic
Found initrd image: /boot/initrd.img-3.19.0-999-generic
Found linux image: /boot/vmlinuz-3.18-3.dmz.2-liquorix-amd64
Found initrd image: /boot/initrd.img-3.18-3.dmz.2-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```kernel is just partially installed and unusable. Only stuff that was changed on it during today's work is update/upgrade and proposed is turned on, as usual for this family of machines...
It doos not generate appropriate image```
$ l -alt /boot
total 68364
drwxr-xr-x  3 root root     4096 &#1112;&#1072;&#1085; 23 14:32 ./
-rw-r--r--  1 root root 19637102 &#1112;&#1072;&#1085; 23 14:32 initrd.img-3.18-3.dmz.2-liquorix-amd64
-rw-r--r--  1 root root 20037776 &#1112;&#1072;&#1085; 23 14:32 initrd.img-3.19.0-999-generic
drwxr-xr-x  5 root root     4096 &#1112;&#1072;&#1085; 23 14:26 grub/
drwxr-xr-x 23 root root     4096 &#1112;&#1072;&#1085; 23 14:24 ../
-rw-r--r--  1 root root  1240419 &#1112;&#1072;&#1085; 23 03:18 abi-3.19.0-999-generic
-rw-r--r--  1 root root   176764 &#1112;&#1072;&#1085; 23 03:18 config-3.19.0-999-generic
-rw-------  1 root root  3750789 &#1112;&#1072;&#1085; 23 03:18 System.map-3.19.0-999-generic
-rw-------  1 root root  6637312 &#1112;&#1072;&#1085; 23 03:18 vmlinuz-3.19.0-999-generic
-rw-r--r--  1 root root   167203 &#1112;&#1072;&#1085; 20 02:23 config-3.18-3.dmz.2-liquorix-amd64
-rw-r--r--  1 root root  2641805 &#1112;&#1072;&#1085; 20 02:23 System.map-3.18-3.dmz.2-liquorix-amd64
-rw-r--r--  1 root root  3331616 &#1112;&#1072;&#1085; 20 02:23 vmlinuz-3.18-3.dmz.2-liquorix-amd64
-rw-r--r--  1 root root  1236259 &#1112;&#1072;&#1085; 18 10:47 abi-3.19.0-031900rc5-generic
-rw-r--r--  1 root root   176520 &#1112;&#1072;&#1085; 18 10:47 config-3.19.0-031900rc5-generic
-rw-------  1 root root  3751093 &#1112;&#1072;&#1085; 18 10:47 System.map-3.19.0-031900rc5-generic
-rw-------  1 root root  6632512 &#1112;&#1072;&#1085; 18 10:47 vmlinuz-3.19.0-031900rc5-generic
-rw-r--r--  1 root root   176500 &#1084;&#1072;&#1088; 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 &#1084;&#1072;&#1088; 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 &#1084;&#1072;&#1088; 12  2014 memtest86+_multiboot.bin
```
If I try manually```
:~$ sudo update-initramfs -c -k 3.19.0-031900rc5-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-031900rc5-generic
W: TMPDIR is mounted noexec, will not cache run scripts.
:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-031900rc5-generic
Found initrd image: /boot/initrd.img-3.19.0-031900rc5-generic
Found linux image: /boot/vmlinuz-3.19.0-999-generic
Found initrd image: /boot/initrd.img-3.19.0-999-generic
Found linux image: /boot/vmlinuz-3.18-3.dmz.2-liquorix-amd64
Found initrd image: /boot/initrd.img-3.18-3.dmz.2-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```
Any ideas? What Am I missing on this machine so that automatic generation fails?
These warnings about NOEXEC (/tmp) were not problem for years... So, I do not suspect that...
Tricky situation because I'll run ot of kernels... ;)
What is default content of /etc/kernel/ folder(s)?

---

### Post by Doug S on 2015-01-23
> **zika said:**
> What is default content of /etc/kernel/ folder(s)?Here is what I had before:```
doug@desk-dev:~$ ls -l /etc/kernel/*
/etc/kernel/postinst.d:
total 16
-rwxr-xr-x 1 root root 2824 Oct  9 21:51 apt-auto-removal
-rwxr-xr-x 1 root root  858 May 31  2012 initramfs-tools
-rwxr-xr-x 1 root root  196 Jul 10  2014 pm-utils
lrwxrwxrwx 1 root root   49 Jan 20 01:39 update-notifier -> /usr/share/update-notifier/notify-reboot-required
-rwxr-xr-x 1 root root  641 Oct 15 05:28 zz-update-grub

/etc/kernel/postrm.d:
total 8
-rwxr-xr-x 1 root root 814 May 31  2012 initramfs-tools
-rwxr-xr-x 1 root root 641 Oct 15 05:28 zz-update-grub
```And I see no difference after trying what you did.

For other readers, here is a normal kernel install, before doing the Zika stuff:```
doug@desk-dev:~$ sudo dpkg -i *3.19*.deb
[sudo] password for doug:
Selecting previously unselected package linux-headers-3.19.0-031900rc5.
(Reading database ... 182980 files and directories currently installed.)
Preparing to unpack linux-headers-3.19.0-031900rc5_3.19.0-031900rc5.201501180935_all.deb ...
Unpacking linux-headers-3.19.0-031900rc5 (3.19.0-031900rc5.201501180935) ...
Selecting previously unselected package linux-headers-3.19.0-031900rc5-generic.
Preparing to unpack linux-headers-3.19.0-031900rc5-generic_3.19.0-031900rc5.201501180935_amd64.deb ...
Unpacking linux-headers-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Selecting previously unselected package linux-image-3.19.0-031900rc5-generic.
Preparing to unpack linux-image-3.19.0-031900rc5-generic_3.19.0-031900rc5.201501180935_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Setting up linux-headers-3.19.0-031900rc5 (3.19.0-031900rc5.201501180935) ...
Setting up linux-headers-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Setting up linux-image-3.19.0-031900rc5-generic (3.19.0-031900rc5.201501180935) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-031900rc5-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-031900rc5-generic /boot/vmlinuz-3.19.0-031900rc5-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-031900rc5-generic
Found initrd image: /boot/initrd.img-3.19.0-031900rc5-generic
Found linux image: /boot/vmlinuz-3.18.0-9-generic
Found initrd image: /boot/initrd.img-3.18.0-9-generic
Found linux image: /boot/vmlinuz-3.16.0-29-generic
Found initrd image: /boot/initrd.img-3.16.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
doug@desk-dev:~$
```O.K. so then I repeat what Zika did (on a disposable VM with 15.04), and I got the same results and am now in the same situation. However, the computer seems to re-boot fine and then seems to run "sudo update-grub" properly. And now I get this when installing a kernel I had lying around:```
doug@desk-dev:~$ sudo dpkg -i *rc3*
Selecting previously unselected package linux-headers-3.18.0-031800rc3.
(Reading database ... 243171 files and directories currently installed.)
Preparing to unpack linux-headers-3.18.0-031800rc3_3.18.0-031800rc3.201411022335_all.deb ...
Unpacking linux-headers-3.18.0-031800rc3 (3.18.0-031800rc3.201411022335) ...
Selecting previously unselected package linux-headers-3.18.0-031800rc3-generic.
Preparing to unpack linux-headers-3.18.0-031800rc3-generic_3.18.0-031800rc3.201411022335_amd64.deb ...
Unpacking linux-headers-3.18.0-031800rc3-generic (3.18.0-031800rc3.201411022335) ...
Selecting previously unselected package linux-image-3.18.0-031800rc3-generic.
Preparing to unpack linux-image-3.18.0-031800rc3-generic_3.18.0-031800rc3.201411022335_amd64.deb ...
Done.
Unpacking linux-image-3.18.0-031800rc3-generic (3.18.0-031800rc3.201411022335) ...
Setting up linux-headers-3.18.0-031800rc3 (3.18.0-031800rc3.201411022335) ...
Setting up linux-headers-3.18.0-031800rc3-generic (3.18.0-031800rc3.201411022335) ...
Setting up linux-image-3.18.0-031800rc3-generic (3.18.0-031800rc3.201411022335) ...
Running depmod.
[COLOR=#ff0000]update-initramfs[/COLOR]: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.18.0-031800rc3-generic /boot/vmlinuz-3.18.0-031800rc3-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.18.0-031800rc3-generic /boot/vmlinuz-3.18.0-031800rc3-generic
[COLOR=#ff0000]update-initramfs:[/COLOR] Generating /boot/initrd.img-3.18.0-031800rc3-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.18.0-031800rc3-generic /boot/vmlinuz-3.18.0-031800rc3-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.18.0-031800rc3-generic /boot/vmlinuz-3.18.0-031800rc3-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.18.0-031800rc3-generic /boot/vmlinuz-3.18.0-031800rc3-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-031900rc5-generic
Found initrd image: /boot/initrd.img-3.19.0-031900rc5-generic
Found linux image: /boot/vmlinuz-3.19.0-999-generic
Found initrd image: /boot/initrd.img-3.19.0-999-generic
Found linux image: /boot/vmlinuz-3.18.0-031800rc3-generic
Found initrd image: /boot/initrd.img-3.18.0-031800rc3-generic
Found linux image: /boot/vmlinuz-3.18.0-9-generic
Found initrd image: /boot/initrd.img-3.18.0-9-generic
Found linux image: /boot/vmlinuz-3.16.0-29-generic
Found initrd image: /boot/initrd.img-3.16.0-29-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
doug@desk-dev:~$
```

---

### Post by zika on 2015-01-23
There is no &#8222;Zika stuff&#8220; in aforementioned stuff... ;)
Now I've resolved it and found culprit: /etc/kernel was cleaned by unknown perpetrator. I'll report after reconstructing it from LiveUSB... ;)
I suspect that perpetrator is *kernel-common* package that I've seen in that users logs and that when purging it contents of */etc/kernel* were cleared. Beware... ;)
Bingo!:```
:/etc/kernel$ ls -alt postinst.d/total 20
drwxr-xr-x 2 root root 4096 &#1112;&#1072;&#1085; 23 18:49 .
lrwxrwxrwx 1 root root   49 &#1112;&#1072;&#1085; 23 18:49 update-notifier -> /usr/share/update-notifier/notify-reboot-required
drwxr-xr-x 4 root root 4096 &#1112;&#1072;&#1085; 23 16:37 ..
-rwxr-xr-x 1 root root  641 &#1112;&#1072;&#1085;  3 13:21 zz-update-grub
-rwxr-xr-x 1 root root 2824 &#1085;&#1086;&#1074;  3 09:12 apt-auto-removal
-rwxr-xr-x 1 root root  858 &#1112;&#1091;&#1085;  1  2012 initramfs-tools
:/etc/kernel$ ls -alt postrm.d/
total 16
drwxr-xr-x 2 root root 4096 &#1112;&#1072;&#1085; 23 18:37 .
drwxr-xr-x 4 root root 4096 &#1112;&#1072;&#1085; 23 16:37 ..
-rwxr-xr-x 1 root root  641 &#1112;&#1072;&#1085;  3 13:21 zz-update-grub
-rwxr-xr-x 1 root root  814 &#1112;&#1091;&#1085;  1  2012 initramfs-tools



```
```
:~$ sudo dpkg -i /tmp/*.debSelecting previously unselected package linux-headers-3.19.0-994.
(Reading database ... 281885 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-994_3.19.0-994.201501230252_all.deb ...
Unpacking linux-headers-3.19.0-994 (3.19.0-994.201501230252) ...
Selecting previously unselected package linux-headers-3.19.0-994-generic.
Preparing to unpack .../linux-headers-3.19.0-994-generic_3.19.0-994.201501230252_amd64.deb ...
Unpacking linux-headers-3.19.0-994-generic (3.19.0-994.201501230252) ...
Selecting previously unselected package linux-image-3.19.0-994-generic.
Preparing to unpack .../linux-image-3.19.0-994-generic_3.19.0-994.201501230252_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-994-generic (3.19.0-994.201501230252) ...
Setting up linux-headers-3.19.0-994 (3.19.0-994.201501230252) ...
Setting up linux-headers-3.19.0-994-generic (3.19.0-994.201501230252) ...
Setting up linux-image-3.19.0-994-generic (3.19.0-994.201501230252) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-994-generic /boot/vmlinuz-3.19.0-994-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-994-generic /boot/vmlinuz-3.19.0-994-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-994-generic
W: TMPDIR is mounted noexec, will not cache run scripts.
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-994-generic /boot/vmlinuz-3.19.0-994-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-994-generic /boot/vmlinuz-3.19.0-994-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-031900rc5-generic
Found initrd image: /boot/initrd.img-3.19.0-031900rc5-generic
Found linux image: /boot/vmlinuz-3.19.0-999-generic
Found initrd image: /boot/initrd.img-3.19.0-999-generic
Found linux image: /boot/vmlinuz-3.19.0-994-generic
Found initrd image: /boot/initrd.img-3.19.0-994-generic
Found linux image: /boot/vmlinuz-3.18.0-9-generic
Found initrd image: /boot/initrd.img-3.18.0-9-generic
Found linux image: /boot/vmlinuz-3.18-3.dmz.2-liquorix-amd64
Found initrd image: /boot/initrd.img-3.18-3.dmz.2-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```
Marking it solved and lesson learned... ;)
[MKUSB]("https://help.ubuntu.com/community/mkusb") helped me a lot today... ;)

---

### Post by Doug S on 2015-01-23
Glad you got it sorted out.

> **zika said:**
> There is no „Zika stuff“ in aforementioned stuff...You're right. What can I say, I messed up interpreting what I was (not) seeing.

---

### Post by syntaxerror74 on 2015-01-23
> **zika said:**
> There is no &#8222;Zika stuff&#8220; in aforementioned stuff... ;)
Now I've resolved it and found culprit: /etc/kernel was cleaned by unknown perpetrator. (...)
I suspect that perpetrator is *kernel-common* package that I've seen in that users logs and that when purging it contents of */etc/kernel* were cleared. Beware... ;)

Thanks for the warning, even though I would not need it.
I always remove (resp. purge) my obsolete kernels by regex and apt-get, e. g. 

```

$ sudo apt-get purge .*3\.16\.0\-28.*
(...)
The following packages will be REMOVED
  linux-headers-3.16.0-28 linux-headers-3.16.0-28-generic linux-image-3.16.0-28-generic
  linux-image-extra-3.16.0-28-generic

```

...and aptitude will get things squeaky-clean for me without damage.
OK, sometimes it might be necessary to run update-grub (recommended), but that's all there is to it.

---


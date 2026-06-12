---
title: "kernal upgrade problems"
date: 2010-12-19
forum: Server Platforms
---

### Post by putz3000 on 2010-12-19
I have a little home server running server 8.04 and decided to check for upgrades.  One of the upgrades was a new kernal update.  It was able to download the update, but errors on uncompressing it.  I have even shutdown the server and restarted it.  Still no luck.

I am not really sure how to proceed.  Here is the screen log from the update process:

(Reading database ... 49993 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-28-server 2.6.24-28.80 (using .../linux-  image-2.6.24-28-server_2.6.24-28.81_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-28-server ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-28-server_2.6.  24-28.81_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.24-28-ser  ver/kernel/drivers/infiniband/hw/cxgb3/iw_cxgb3.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-28-server
Found kernel: /boot/vmlinuz-2.6.24-26-server
Found kernel: /boot/vmlinuz-2.6.24-24-server
Found kernel: /boot/vmlinuz-2.6.24-23-server
Found kernel: /boot/vmlinuz-2.6.24-22-server
Found kernel: /boot/vmlinuz-2.6.24-19-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-28-server_2.6.24-28.81_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2010-12-19
From Applications > Accessories > Terminal, try,

```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Please post the output of all those commands and while posting, click the # icon in post menu and paste your text in between the generated code tags.

---


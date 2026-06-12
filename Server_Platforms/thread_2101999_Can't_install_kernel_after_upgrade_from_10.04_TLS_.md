---
title: "Can't install kernel after upgrade from 10.04 TLS to 12.04 TLS"
date: 2013-01-06
forum: Server Platforms
---

### Post by Fraaik on 2013-01-06
Hello guys!

I run into troubles after upgrade from 10.04 TLS to 12.02 TLS.
All went fine until the last step: therefore my boot is too small.

I think can not delete any file from boot. (or, what do you think?) It looks like this:

```

ls -l /boot
total 16727
-rw-r--r-- 1 root root   654985 Sep 16  2010 abi-2.6.32-24-generic-pae
-rw-r--r-- 1 root root   116360 Sep 16  2010 config-2.6.32-24-generic-pae
drwxr-xr-x 3 root root     7168 Dez 30 19:25 grub
-rw-r--r-- 1 root root 10016895 Dez 27 17:00 initrd.img-2.6.32-24-generic-pae
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  1730172 Sep 16  2010 System.map-2.6.32-24-generic-pae
-rw-r--r-- 1 root root     1200 Sep 16  2010 vmcoreinfo-2.6.32-24-generic-pae
-rw-r--r-- 1 root root  4167840 Sep 16  2010 vmlinuz-2.6.32-24-generic-pae

```I tried to resize my boot partition with gparted but it didn't work:
it still sticks to 285MB even though there are 500MB unused disk space.

My disk layout is:

```

df
Filesystem     1K-blocks   Used Available Use% Mounted on
/dev/sda1         282599 206303     61704  77% /
udev             1020508      4   1020504   1% /dev
tmpfs             410296    460    409836   1% /run
none                5120      0      5120   0% /run/lock
none             1025736      0   1025736   0% /run/shm
/dev/sda8         960504  17616    894096   2% /tmp
/dev/sda9       90065056 275528  85214400   1% /home
/dev/sda5       19223252 843300  17403468   5% /usr
/dev/sda6       37941612 418044  35596000   2% /var

```Is there anyone who have an advice for me what I can do?

Thank you and cheers,
Fraaik

---


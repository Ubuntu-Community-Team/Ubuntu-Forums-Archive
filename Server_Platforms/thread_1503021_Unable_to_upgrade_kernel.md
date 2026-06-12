---
title: "Unable to upgrade kernel"
date: 2010-06-06
forum: Server Platforms
---

### Post by jimwillsher on 2010-06-06
Hi all,

Can anyone diagnose this please?

```

Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release.gpg
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com lucid-security Release
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release
Hit http://gb.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://gb.archive.ubuntu.com lucid/main Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://gb.archive.ubuntu.com lucid/restricted Packages
Hit http://gb.archive.ubuntu.com lucid/main Sources
Hit http://gb.archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/universe Packages
Hit http://gb.archive.ubuntu.com lucid/universe Sources
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://debian.slimdevices.com stable Release.gpg
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://debian.slimdevices.com/ stable/main Translation-en_GB
Get: 1 http://debian.slimdevices.com stable Release [1,645B]
Ign http://debian.slimdevices.com stable/main Packages
Ign http://debian.slimdevices.com stable/main Packages
Hit http://debian.slimdevices.com stable/main Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-2.6.32-22 linux-headers-2.6.32-22-server linux-image-2.6.32-22-server
The following packages will be upgraded:
  linux-headers-server linux-image-server linux-server
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.6MB of archives.
After this operation, 210MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-22-server 2.6.32-22.36 [30.9MB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-22 2.6.32-22.36 [9,868kB]
Get: 3 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-22-server 2.6.32-22.36 [748kB]
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-server 2.6.32.22.23 [3,964B]
Get: 5 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-server 2.6.32.22.23 [3,968B]
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-server 2.6.32.22.23 [3,974B]
Fetched 41.6MB in 49s (844kB/s)
Selecting previously deselected package linux-image-2.6.32-22-server.
(Reading database ... 50996 files and directories currently installed.)
Unpacking linux-image-2.6.32-22-server (from .../linux-image-2.6.32-22-server_2.6.32-22.36_amd64.deb) ...
Done.
Selecting previously deselected package linux-headers-2.6.32-22.
Unpacking linux-headers-2.6.32-22 (from .../linux-headers-2.6.32-22_2.6.32-22.36_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-22-server.
Unpacking linux-headers-2.6.32-22-server (from .../linux-headers-2.6.32-22-server_2.6.32-22.36_amd64.deb) ...
Preparing to replace linux-headers-server 2.6.32.21.22 (using .../linux-headers-server_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Preparing to replace linux-server 2.6.32.21.22 (using .../linux-server_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-server ...
Preparing to replace linux-image-server 2.6.32.21.22 (using .../linux-image-server_2.6.32.22.23_amd64.deb) ...
Unpacking replacement linux-image-server ...
Setting up linux-image-2.6.32-22-server (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-server
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-server
Found initrd image: /boot/initrd.img-2.6.32-22-server
Found linux image: /boot/vmlinuz-2.6.32-21-server
Found initrd image: /boot/initrd.img-2.6.32-21-server
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04 LTS (10.04) on /dev/sda1
done

[b]Setting up linux-headers-2.6.32-22 (2.6.32-22.36) ...
dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': Invalid argument
E: Sub-process /usr/bin/dpkg returned an error code (2)
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/b]






root@music:/var/lib/dpkg# dpkg --configure -a
Setting up linux-image-server (2.6.32.22.23) ...
Setting up linux-server (2.6.32.22.23) ...
Setting up linux-headers-2.6.32-22 (2.6.32-22.36) ...
Setting up linux-headers-2.6.32-22-server (2.6.32-22.36) ...

Setting up linux-headers-server (2.6.32.22.23) ...

```



This has just happened today, previous updates have all seemed okay.

Many thanks,



Jim

---


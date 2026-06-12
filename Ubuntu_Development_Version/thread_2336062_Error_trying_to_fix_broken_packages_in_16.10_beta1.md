---
title: "Error trying to fix broken packages in 16.10 beta1"
date: 2016-09-04
forum: Ubuntu Development Version
---

### Post by Devon_suz on 2016-09-04
I tried a update and received a broken packages  notice. I tried apt-get install -f to fix the broken packages. The result I received was the following. I  also tried to remove the two packages 
Removing grub-efi-amd64-signed (1.73+2.02~beta2-36ubuntu10)   shim-signed. This is a multi-booting system with Windows 10 ,Ubuntu 16.04 and Linux Mont 18. Since windows is on the system I assumed uefi was used ( but I know that is dangerous to assume) 

Any help appreciated. I was installed  in compatibility mode

    sudo apt-get install -f[sudo] password
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 111 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up shim-signed (1.20+0.9+1465500757.14a5905-0ubuntu1) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.73+2.02~beta2-36ubuntu10) ...
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ventrical on 2016-09-04
Hi,

```


sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a

and again
sudo apt-get install -f

```

```

sudo apt-get update
sudo apt-get dist-upgrade

```

regards..

---

### Post by grahammechanical on 2016-09-04
We are also asuuming that you are running this update from Ubuntu 16.10 and not Linux Mint 18. You can open the file manager and browse to /usr/lib/grub/i386-pc/ and look for modinfo.sh. It will be a script file. I have one on my BIOS boot system installation. The error is that modinfo.sh does not exist. As this is a 16.10 install a re-install might be the easiest solution.

Regards.

---


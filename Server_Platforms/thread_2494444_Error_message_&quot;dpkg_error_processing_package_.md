---
title: "Error message &quot;dpkg: error processing package linux-image-5.4.0-137-generic&quot;"
date: 2024-01-17
forum: Server Platforms
---

### Post by hjlee2 on 2024-01-17
After rebooting my ubuntu server, the following message appears for all the apt and apt-get commands.


dpkg: error processing package linux-image-5.4.0-137-generic


I've tried various commands including:


```

1. sudo apt update && sudo apt upgrade
2. sudo apt full-upgrade
3. sudo dpkg --purge linux-image-5.4.0-137-generic
4. sudo dpkg --configure -a
5. sudo apt install -f
6. sudo apt update && sudo apt dist-upgrade -y

```


However, the commands generate the same error message:


```

Removing linux-image-5.4.0-137-generic (5.4.0-137.154) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-137-generic
/etc/kernel/postrm.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-5.4.0-74-generic
Found kernel: /vmlinuz-4.15.0-192-generic
Found kernel: /vmlinuz-4.15.0-189-generic
run-parts: /etc/kernel/postrm.d/x-grub-legacy-ec2 exited with return code 10
dpkg: error processing package linux-image-5.4.0-137-generic (--remove):
installed linux-image-5.4.0-137-generic package post-removal script subprocess returned error exit status 1

```


Can anyone help?


Thanks in advance.

---

### Post by slickymaster on 2024-01-17
Thread moved to **Server Platforms** for a better fit

---

### Post by MAFoElffen on 2024-01-17
I just spun up an instance of Server 20.04.6 as Legacy Boot... It installed with (only) Kernel 5.4.0-169.

Doing an apt list, I found that was the current kernel. The next older was 5.4.0-167 (There was no -168).

On yours I see:
```

5.4.0-167-generic
5.4.0-74-generic
4.15.0-192-generic
4.15.0-189-generic

```
I don't know why you are trying to remove it.

But, for my own entertainment, what happens if you do
```

sudo apt install --yes linux-image-5.4.0-137-generic linux-headers-5.4.0-137-generic linux-modules-5.4.0-137-generic linux-modules-extra-5.4.0-137-generic

```
To ensure all the pieces of that are there.

---

### Post by hjlee2 on 2024-01-17
Thanks a lot.

Actually, I'm not trying to remove the kernel. 

But everytime I'm trying to install a package using apt, the error message appears.

After running the code, the following error message appears.

```

DKMS: build completed.


nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-peermem.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


depmod...


DKMS: install completed.
   ...done.
Processing triggers for linux-image-5.4.0-169-generic (5.4.0-169.187) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-169-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-169-generic
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-5.4.0-74-generic
Found kernel: /vmlinuz-4.15.0-192-generic
Found kernel: /vmlinuz-4.15.0-189-generic
run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 10
dpkg: error processing package linux-image-5.4.0-169-generic (--configure):
 installed linux-image-5.4.0-169-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-modules-extra-5.4.0-137-generic
 openssh-server
 ufw
 nfs-common
 linux-image-5.4.0-169-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by MAFoElffen on 2024-01-17
> **hjlee2 said:**
> 
After rebooting my ubuntu server, the following message appears for all the apt and apt-get commands.


> **hjlee2 said:**
> 
nvidia.ko:
...
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/

nvidia-uvm.ko:
...
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/

nvidia-modeset.ko:
...
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-drm.ko:
...
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/


nvidia-peermem.ko:
...
   - Installing to /lib/modules/5.4.0-137-generic/updates/dkms/

DKMS: install completed.
   ...done.

Processing triggers for linux-image-5.4.0-169-generic (5.4.0-169.187) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-169-generic
   ...done.

/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-169-generic
...
Found kernel: /vmlinuz-5.4.0-74-generic
Found kernel: /vmlinuz-4.15.0-192-generic
Found kernel: /vmlinuz-4.15.0-189-generic
[COLOR=#ff0000]run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 10[/COLOR]

dpkg: error processing package linux-image-5.4.0-169-generic (--configure):
 installed linux-image-5.4.0-169-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-modules-extra-5.4.0-137-generic
 openssh-server
 ufw
 nfs-common
 linux-image-5.4.0-169-generic

Why does your Server have NVidia? No matters...

Do this please:
```

sudo rm /boot/grub/menu.lst 
sudo rm /etc/kernel/postrm.d/x-grub-legacy-ec2
sudo rm /boot/grub/default
sudo dpkg --configure -a
sudo apt install --reinstall grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common
sudo dpkg-reconfigure grub-pc

```

---

### Post by hjlee2 on 2024-01-18
After running
```

sudo dpkg --configure -a

```

I get the following error msg.
```

Setting up openssh-server (1:8.2p1-4ubuntu0.11) ...
dpkg: error processing package openssh-server (--configure):
 installed openssh-server package post-installation script subprocess returned error exit status 10
Setting up linux-image-5.4.0-169-generic (5.4.0-169.187) ...
Setting up ufw (0.36-6ubuntu1.1) ...
dpkg: error processing package ufw (--configure):
 installed ufw package post-installation script subprocess returned error exit status 10
Setting up nfs-common (1:1.3.4-2.5ubuntu3.5) ...
dpkg: error processing package nfs-common (--configure):
 installed nfs-common package post-installation script subprocess returned error exit status 10
Setting up grub-pc (2.04-1ubuntu26.17) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of grub-gfxpayload-lists:
 grub-gfxpayload-lists depends on grub-pc (>= 1.99~20101210-1ubuntu2); however:
  Package grub-pc is not configured yet.




dpkg: error processing package grub-gfxpayload-lists (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-5.4.0-169-generic (5.4.0-169.187) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-169-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-169-generic
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 10
dpkg: error processing package linux-image-5.4.0-169-generic (--configure):
 installed linux-image-5.4.0-169-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 openssh-server
 ufw
 nfs-common
 grub-pc
 grub-gfxpayload-lists
 linux-image-5.4.0-169-generic

```

Also, after running 
```

sudo apt install --reinstall grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common

```

I get the following error
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 5 not upgraded.
6 not fully installed or removed.
Need to get 0 B/3,433 kB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for grub-pc:amd64

```

---

### Post by MAFoElffen on 2024-01-18
This is what I get. Try the same on yours...
```

mafoelffen@msi-ubuntu:~/Scripts$ apt list grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common
Listing... Done
grub-common/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic]
grub-common/jammy-updates 2.06-2ubuntu7.2 i386
grub-gfxpayload-lists/jammy 0.7 amd64
grub-pc-bin/jammy-updates 2.06-2ubuntu7.2 amd64
grub-pc/jammy-updates,now 2.06-2ubuntu7.2 amd64 [residual-config]
grub2-common/jammy-updates,now 2.06-2ubuntu7.2 amd64 [installed,automatic]
grub2-common/jammy-updates 2.06-2ubuntu7.2 i386

```
Reinstall those packages and then reconfigure them.

---

### Post by hjlee2 on 2024-01-18
The following code works, but I still get the same error after 
```

sudo apt install --reinstall grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common

```

---

### Post by MAFoElffen on 2024-01-19
Dang. That is persistent isn't it?

What does this show?
```

apt list linux-*-generic --installed

```

---

### Post by hjlee2 on 2024-01-24
Sorry, I was out for a few days.

Yes, the same error appears for all the apt-get install commands.

This is what I get.

```

Listing... Done
linux-headers-5.15.0-46-generic/focal-updates,focal-security,now 5.15.0-46.49~20.04.1 amd64 [installed]
linux-headers-5.4.0-137-generic/focal-updates,focal-security,now 5.4.0-137.154 amd64 [installed]
linux-headers-5.4.0-169-generic/focal-updates,focal-security,now 5.4.0-169.187 amd64 [installed,automatic]
linux-headers-generic/focal-updates,focal-security,now 5.4.0.169.167 amd64 [installed,automatic]
linux-image-5.15.0-46-generic/focal-updates,focal-security,now 5.15.0-46.49~20.04.1 amd64 [installed]
linux-image-5.4.0-169-generic/focal-updates,focal-security,now 5.4.0-169.187 amd64 [installed,automatic]
linux-image-generic/focal-updates,focal-security,now 5.4.0.169.167 amd64 [installed,automatic]
linux-modules-5.15.0-46-generic/focal-updates,focal-security,now 5.15.0-46.49~20.04.1 amd64 [installed,automatic]
linux-modules-5.4.0-137-generic/focal-updates,focal-security,now 5.4.0-137.154 amd64 [installed]
linux-modules-5.4.0-169-generic/focal-updates,focal-security,now 5.4.0-169.187 amd64 [installed,automatic]
linux-modules-extra-5.4.0-169-generic/focal-updates,focal-security,now 5.4.0-169.187 amd64 [installed,automatic]
linux-tools-5.15.0-46-generic/focal-updates,focal-security,now 5.15.0-46.49~20.04.1 amd64 [installed]
linux-tools-5.4.0-137-generic/focal-updates,focal-security,now 5.4.0-137.154 amd64 [installed]
linux-tools-5.4.0-169-generic/focal-updates,focal-security,now 5.4.0-169.187 amd64 [installed,automatic]
linux-tools-generic/focal-updates,focal-security,now 5.4.0.169.167 amd64 [installed]

```

---

### Post by hjlee2 on 2024-01-24
Can the following link be a potential solution?

[https://forums.linuxmint.com/viewtopic.php?t=361469](https://forums.linuxmint.com/viewtopic.php?t=361469)

---

### Post by MAFoElffen on 2024-01-25
You never showed my the outpu from this, that I asked for in Post #7:
```

apt list grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common

```
What part of that are you refering to? That is a long thread. Please give me a Post # to start reading from...

---

### Post by hjlee2 on 2024-02-07
Oh sorry, I'm new to this forum.

I did not know there was an additional page...

After using
```

apt list grub-common grub-gfxpayload-lists  grub-pc grub-pc-bin grub2-common

```

I get,
```

grub-common/focal-updates,now 2.04-1ubuntu26.17 amd64 [installed,automatic]
grub-gfxpayload-lists/focal,now 0.7 amd64 [installed,automatic]
grub-pc-bin/focal-updates,now 2.04-1ubuntu26.17 amd64 [installed,automatic]
grub-pc/focal-updates,now 2.04-1ubuntu26.17 amd64 [installed]
grub2-common/focal-updates,now 2.04-1ubuntu26.17 amd64 [installed,automatic]

```

---

### Post by MAFoElffen on 2024-02-08
From your earlier post where you said you got the last error:
```

E: Internal Error, No file name for grub-pc:amd64

```
But from the output:
```

grub-pc/focal-updates,now 2.04-1ubuntu26.17 amd64 [installed]

```
Time to file a bug report.

There is something going on there under the covers that does not make sense.

It has those files. Yet it is throwing errors on things that are confirmed as there. You have done nothing to cause this. You have done your due diligence to correct it, yet things are still going on.

---

### Post by hjlee2 on 2024-02-12
Alright I see.

Thanks a lot for your comments!

It was of a great help.

---

### Post by MAFoElffen on 2024-02-13
> **hjlee2 said:**
> Alright I see.

Thanks a lot for your comments!

It was of a great help.
Did you file a bug report at LaunchPad? If so, please post the link to it in this thread so we can follow the progress. I really am curious to what is going on causing this.

---


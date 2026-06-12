---
title: "Problem With Virtualbox"
date: 2017-03-11
forum: Virtualisation
---

### Post by shane_faulkinbury2 on 2017-03-11
I'm having all kinds of problems loading Windows 10 on Virtualbox.   First of I get a message telling me I have to do a.[PHP]sbin/vboixconfig[/PHP].  When I do that I notice I have to install mysql-server and mysql-server 5.7.  This all started when I installed kernel  4.10.1 on Ubuntu.  So if you know how to go back a kernel version or you can help me install mysql-server 5.7  that would be great so I can get Virtualbox going.

---

### Post by wildmanne39 on 2017-03-12
*Thread moved to **Virtualisation**.*

---

### Post by DuckHook on 2017-03-12
You probably don't want to install mysql just to get VBox running. That's very Rube Goldbergish and bringing in a complex machine just to pour a cup of coffee. Increased complexity, attack surface, more things to go wrong, and all that.

[LIST=1]
[*]What version of Ubuntu are you using?
[*]What flavour?
[*]How did you install the new kernel?
[*]Why did you install it?
[*]Did you need it for a new piece of equipment?
[/LIST]
You must provide far more background info. Such details are necessary to understand your current setup before anyone can help.

Also, post results of the following:```
dpkg --get-selections | grep linux
``````
ls -laH /boot
```

---

### Post by shane_faulkinbury2 on 2017-03-12
Xbuntu 16.04 and I installed the same way this site did on a 64 bit.  [HTML]http://ubuntuhandbook.org/index.php/2016/05/install-linux-kernel-4-6-ubuntu-16-04/[/HTML]
```
console-setup-linux				installextlinux					install
libselinux1:amd64				install
libselinux1:i386				install
linux-base					install
linux-firmware					install
linux-headers-4.10.1-041001			install
linux-headers-4.4.0-66				install
linux-headers-4.4.0-66-generic			install
linux-headers-4.8.0-36				install
linux-headers-4.8.0-36-generic			install
linux-headers-4.8.0-39				install
linux-headers-4.8.0-39-generic			install
linux-headers-generic				install
linux-image-4.10.1-041001-generic		install
linux-image-4.8.0-36-generic			install
linux-image-4.8.0-39-generic			install
linux-image-4.8.0-41-generic			deinstall
linux-image-extra-4.8.0-36-generic		install
linux-image-extra-4.8.0-39-generic		install
linux-image-extra-4.8.0-41-generic		deinstall
linux-libc-dev:amd64				install
linux-signed-image-4.8.0-36-generic		deinstall
linux-signed-image-4.8.0-39-generic		deinstall
linux-signed-image-4.8.0-41-generic		deinstall
linux-sound-base				install
pptp-linux					install
python3-selinux					install
syslinux					install
syslinux-common					install
syslinux-legacy					install
util-linux					install



```
```
total 177376drwxr-xr-x  5 root root     3072 Mar 12 09:08 .
drwxr-xr-x 25 root root     4096 Mar 12 09:08 ..
-rw-r--r--  1 root root  1413958 Feb 26 07:48 abi-4.10.1-041001-generic
-rw-r--r--  1 root root  1407843 Feb  5 06:32 abi-4.8.0-36-generic
-rw-r--r--  1 root root  1408261 Feb 20 13:42 abi-4.8.0-39-generic
-rw-r--r--  1 root root   203874 Feb 26 07:48 config-4.10.1-041001-generic
-rw-r--r--  1 root root   199575 Feb  5 06:32 config-4.8.0-36-generic
-rw-r--r--  1 root root   199575 Feb 20 13:42 config-4.8.0-39-generic
drwx------  3 root root     4096 Dec 31  1969 efi
drwxr-xr-x  5 root root     1024 Mar 12 09:08 grub
-rw-r--r--  1 root root 41144908 Mar 10 10:43 initrd.img-4.10.1-041001-generic
-rw-r--r--  1 root root 42762442 Feb 19 09:32 initrd.img-4.8.0-36-generic
-rw-r--r--  1 root root 43016450 Feb 27 21:36 initrd.img-4.8.0-39-generic
drwx------  2 root root    12288 Feb 18 23:47 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3695319 Feb 26 07:48 System.map-4.10.1-041001-generic
-rw-------  1 root root  4060748 Feb  5 06:32 System.map-4.8.0-36-generic
-rw-------  1 root root  4067758 Feb 20 13:42 System.map-4.8.0-39-generic
-rw-------  1 root root  7513872 Feb 26 07:48 vmlinuz-4.10.1-041001-generic
-rw-r--r--  1 root root  7297312 Feb 18 23:49 vmlinuz-4.8.0-36-generic
-rw-r--r--  1 root root  7299224 Feb 15 16:38 vmlinuz-4.8.0-36-generic.efi.signed
-rw-------  1 root root  7311872 Feb 20 13:42 vmlinuz-4.8.0-39-generic
-rw-------  1 root root  7313784 Feb 21 21:57 vmlinuz-4.8.0-39-generic.efi.signed



```

---

### Post by shane_faulkinbury2 on 2017-03-12
Thanks for your help, but I fixed the problem on my own.

I simply held the shift key down while rebooting and reverted back to my original kernel.  The kernel upgrade seems to be the problem because Virtualbox is running fine now with Windows 10 loaded.  Guess I'll just wait for 17.04 to be released before I get the new kernel.  :P

---

### Post by DuckHook on 2017-03-12
Yes, I suspected your problem might be an incompatible new kernel, but wanted to see exactly what you have on your system first.

It seems that you are missing a lot of default kernel elements for a 16.04 installation including *linux-generic* and *linux-generic-hwe-16.04*. Yet you have both the 4.4 kernel and 4.8 kernel installed. I assume that you've gone so far off the beaten track that you are no longer getting automatic updates?

While it is up to you what you want to do with your OS, you may wish to keep things more properly structured. It appears that you've installed kernels without the supporting infrastructure that must accompany them to keep you out of trouble.

At this point, I would suggest the following:

[LIST=1]
[*]Purge the 4.10 kernel from your system altogether:```
sudo apt purge linux-image-4.10.1-041001-generic linux-headers-4.10.1-041001
``````
sudo update-grub
```
[*]Since you are clearly already running the 4.8 kernel, install it properly along with the full hardware enablement stack:```
sudo apt install --install-recommends xserver-xorg-hwe-16.04
```Reboot
[*]Do a proper wash & rinse cycle with:```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```Reboot
[/LIST]
Not to harp on it, but there is nothing to be gained from jumping the gun on new kernels unless you have bleeding-edge HW that's misbehaving with the proper kernels. Doing what you did just ends up breaking your system—or even worse—creating odd OS behaviour like yours that is sometimes impossible to diagnose. Unless you are testing new kernels for the development team (in which case, why are you using Xenial?), it's best to stick with what works, especially if this is your production box. ;)

Good Luck and Happy Ubuntu-ing!

---


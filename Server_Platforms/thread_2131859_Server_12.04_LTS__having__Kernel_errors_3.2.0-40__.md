---
title: "Server 12.04 LTS  having  Kernel errors 3.2.0-40  but showing 3.5.0-27"
date: 2013-04-03
forum: Server Platforms
---

### Post by oldschoolgentoo on 2013-04-03
```
$ grub-install -v
/usr/sbin/grub-install: 11: /etc/default/grub: used: not found
grub-install (GRUB) 1.99-21ubuntu3.9

```

```
$ uname -r
3.2.0-39-generic

```

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
```

Nix Box is  ---   Dell Precision 690 Server      (4) Intel(R) Xeon(R) CPU            5150  @ 2.66GHz     16GB Ram

```
$ sudo dpkg --configure -a
Setting up linux-image-3.2.0-40-generic (3.2.0-40.64) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: used: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-40-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-40-generic; however:
  Package linux-image-3.2.0-40-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.5.0-27-generic (3.5.0-27.46~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: used: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postinst line 1010.
dpkg: error processing linux-image-3.5.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-40-generic; however:
  Package linux-image-3.2.0-40-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.40.48); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.40.48); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-27-generic; however:
  Package linux-image-3.5.0-27-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-image-generic-lts-quantal; however:
  Package linux-image-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-40-generic
 linux-image-generic
 linux-image-3.5.0-27-generic
 linux-image-server
 linux-server
 linux-generic
 linux-image-generic-lts-quantal
 linux-generic-lts-quantal
```




```

linux-server depends on linux-image-server (= 3.2.0.40.48); however:   Package linux-image-server is not configured yet.
```

[B]
My question is why is my system trying to install or use 3.5.0-27 instead of the installed  3.2.0-40 kernel?[/B]

Not really wanting to upgrade my dist. to 12.10  been very happy with 12.04 LTS

mostly want to either upgrade the kernel to 3.5  or  go back to 3.2.

been doing some research on kernel issues,  50% are pushing "GUI package managers" to fix.  Tried to use it to install "meta packages"  but it returned the same error as the large section of CODE in middle of post. So after trying to wade through Hundreds of posts dating as far back as 2009,  I decided to post my issue,  and im hoping its not a BUG issue either.  ughhh

---

### Post by oldschoolgentoo on 2013-04-05
Ok,   now  a bit of update.    I found some of the issues from this post.   I have installed on the Server the Nvidia Quadro FX550,  this being said it needs the 304 driver not 310 version.  Compounded to that it requires the  3.2.0-40 Kernel not the 3.5 that is installed presently on 12.04 LTS.  

now  after a clean  install of 12.04 LTS Server last night,  I wake to this moring of adding a Gnome Desktop for the Kid to use for school work.  The System is freezing.  as i have been reading alot about recently. hopefully i can compelete this post before it freezes.


Now to locate the cause of the freeze.    System is clean  no extra fluff  just going to chase as i go.

---


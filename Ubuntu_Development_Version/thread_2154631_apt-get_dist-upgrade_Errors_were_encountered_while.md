---
title: "apt-get dist-upgrade: Errors were encountered while processing:"
date: 2013-06-15
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-06-15
Anyone have a clue?

```
update-initramfs: Generating /boot/initrd.img-3.9.0-6-generic
Errors were encountered while processing:
 udev
 systemd-services
 libpam-systemd:amd64
 network-manager
 gnome-bluetooth
 xserver-xorg-core
 xserver-xorg-video-intel
 xserver-xorg-video-modesetting
 xserver-xorg-video-nouveau
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

This is a U+1 amd64 installed on June 15 and updated every couple days.

---

### Post by Chanath on 2013-06-15
I have also got an error. Startup Applications doesn't appear at all.

---

### Post by jerrylamos on 2013-06-15
Rebooted.
1. Xorg screwed up, sluggish display not right but usable.  Keyboard very sluggish.
2. Internal error trying to start nm applet.  Of course can't report a launchpad error since nm doesn't work.
3. Systems Settings > Network Manager:  "Network manager is not compatible with this version" or something close to that.  Comes up with a "Proxy" screen??
4. No network no way to try to fix anything.
5. Restart did a logout instead, very very sluggish, then start at 1. above.
6. Launcher sick.
7. Ctrl-Alt-t sudo reboot worked.

This is a 5 June install of U+1 vs. the sick 15 June install.  Do Not Update until forum indicates someone is having success.

I'll do a sudo update-grub, grub-install /dev/sdb (USB SSD) and a zsync to get ready to replace the sick partition.

---

### Post by jerrylamos on 2013-06-16
Since the install was thoroughly botched by ubuntu's update, I did a re-install.  Running O.K.  
Typical U+1, running fine until a dread update.  Let the buyer beware....

---

### Post by jerrylamos on 2013-06-17
On my desktop, totally different intel hardware than the topic, did i386 desktop apt-get update, apt-get dist-upgrade from 3.9.0-4 to 3..0-6 very similar error messages as in the topic, xorg and network manager update errors. Oops, is another install disabled??

While still connected to the  internet did a quick apt-get -f install which did a bunch of un-intelligible stuff to me and was then able to re-boot O.K.  Whew.

---

### Post by jerrylamos on 2013-06-17
Errors on third pc, a notebook, Acer Aspire 5253 on updating from rc4 to rc6:
update, dist-upgrade wound up with 8 not installed.  Did apt-get -f install did something or other now able to run O.K.

Setting up udev (204-0ubuntu4) ...
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 1
...
Setting up libsystemd-daemon0:amd64 (204-0ubuntu4) ...
dpkg: dependency problems prevent configuration of systemd-services:
 systemd-services depends on udev (>= 175-0ubuntu23); however:
  Package udev is not configured yet.

dpkg: error processing systemd-services (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd-services (= 204-0ubuntu4); however:
  Package systemd-services is not configured yet.

dpkg: error processing libpam-systemd:amd64 (--configure):
.....
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.

dpkg: error processing xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-modesetting:
 xserver-xorg-video-modesetting depends on xorg-video-abi-13; however:
  Package xorg-video-abi-13 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-13 is not configured yet.
 xserver-xorg-video-modesetting depends on xserver-xorg-core (>= 2:1.12.99.901); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing xserver-xorg-video-modesetting (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xserver-xorg-video-nouveau:
 xserver-xorg-video-nouveau depends on xorg-video-abi-13; however:
  Package xorg-video-abi-13 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-13 is not configured yet.
 xserver-xorg-video-nouveau depends on xserver-xorg-core (>= 2:1.12.99.901); however:
  Package xserver-xorg-core is not configured yet.

dpkg: error processing xserver-xorg-video-nouveau (--configure):
 dependency problems - leaving unconfigured
Setting up libpeas-common (1.8.0-1ubuntu2) ...
No apport report written because MaxReports is reached already
.....
Errors were encountered while processing:
 udev
 systemd-services
 libpam-systemd:amd64
 network-manager
 gnome-bluetooth
 xserver-xorg-core
 xserver-xorg-video-modesetting
 xserver-xorg-video-nouveau
E: Sub-process /usr/bin/dpkg r
....
jerry@Aspire-5253:~$ sudo apt-get -f install
[sudo] password for jerry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up udev (204-0ubuntu4) ...
udev stop/waiting
udev start/running, process 31983
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up systemd-services (204-0ubuntu4) ...
Setting up libpam-systemd:amd64 (204-0ubuntu4) ...
Setting up network-manager (0.9.8.0-0ubuntu11) ...
Setting up gnome-bluetooth (3.6.1-0ubuntu4) ...
Setting up xserver-xorg-core (2:1.13.3-0ubuntu13) ...
Setting up xserver-xorg-video-modesetting (0.8.0-0ubuntu1) ...
Setting up xserver-xorg-video-nouveau (1:1.0.8-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.9.0-6-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jerry@Aspire-5253:~$

---

### Post by jerrylamos on 2013-06-17
Couple hours later did update, dist-upgrade went clean with two packages updated, libparted0debian1 parted
Went O.K.  Note, df shows more and more space used in spite of purge, remove, autoremove etc. so will think about doing an install to clean up dead code.

---

### Post by zika on 2013-06-17
> **jerrylamos said:**
> Couple hours later did update, dist-upgrade went clean with two packages updated, libparted0debian1 parted
Went O.K.  Note, df shows more and more space used in spite of purge, remove, autoremove etc. so will think about doing an install to clean up dead code.
What &#8222;dead code&#8220; are You refering to?
Did You consider logs, caches and similar?

---

### Post by jerrylamos on 2013-06-17
> **zika said:**
> What &#8222;dead code&#8220; are You refering to?
Did You consider logs, caches and similar?Whatever balloons up the Used disk space from, say, 3,200,000 kb to 3,861,328 kb.  When "used" gets up toward 4,000,000 I re-install.  Now I've got plenty of GB but there are usually 3 or 4 bootable ubuntu partitions per hard drive here, say, unstable, unstable a little older, stable, LTS.

Oops, just did another update - last one was yesterday - now 3898132 after apt-get remove, apt-get auto-remove, and of course 3.9.0-4 was apt-get purged yesterday.

---

### Post by zika on 2013-06-18
> **jerrylamos said:**
> Whatever balloons up the Used disk space from, say, 3,200,000 kb to 3,861,328 kb.  When "used" gets up toward 4,000,000 I re-install.  Now I've got plenty of GB but there are usually 3 or 4 bootable ubuntu partitions per hard drive here, say, unstable, unstable a little older, stable, LTS.

Oops, just did another update - last one was yesterday - now 3898132 after apt-get remove, apt-get auto-remove, and of course 3.9.0-4 was apt-get purged yesterday.Any use of these installs other than tracking disk usage and reinstall?

---


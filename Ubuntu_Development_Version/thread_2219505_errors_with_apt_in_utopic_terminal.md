---
title: "errors with apt in utopic terminal?"
date: 2014-04-24
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-24
Just tried to install fvwm-crystal in Terminal and got the following errors:

```

ventrical@ventrical-desktop:~$ sudo apt-get install fvwm-crystal
[sudo] password for ventrical: 
Reading package lists... Error!
E: Problem renaming the file /var/cache/apt/pkgcache.bin.ygYWBn to /var/cache/apt/pkgcache.bin - rename (2: No such file or directory)
W: You may want to run apt-get update to correct these problems
ventrical@ventrical-desktop:~$ 


```

but it worked just fine in synaptic.

---

### Post by slickymaster on 2014-04-24
With 3.15.0-031500rc2-generic kernel over here. Didn't use fvwm-crystal because of the amount of extra packages it would bring with it, but test it to install mousepad and nothing went wrong:```
~$ sudo apt-get install mousepad 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mousepad
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 202 kB of archives.
After this operation, 888 kB of additional disk space will be used.
Get:1 http://pt.archive.ubuntu.com/ubuntu/ utopic/universe mousepad i386 0.3.0-2 [202 kB]
Fetched 202 kB in 1s (103 kB/s)    
Selecting previously unselected package mousepad.
(Reading database ... 187757 files and directories currently installed.)
Preparing to unpack .../mousepad_0.3.0-2_i386.deb ...
Unpacking mousepad (0.3.0-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up mousepad (0.3.0-2) ...
```

---

### Post by ventrical on 2014-04-24
Logged out and back in again:

```

ventrical@ventrical-desktop:~$ sensors
The program 'sensors' is currently not installed. You can install it by typing:
sudo apt-get install lm-sensors
ventrical@ventrical-desktop:~$ sudo apt-get install lm-sensors
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-14 linux-headers-3.13.0-14-generic
  linux-headers-3.13.0-19 linux-headers-3.13.0-19-generic
  linux-image-3.13.0-14-generic linux-image-3.13.0-19-generic
  linux-image-extra-3.13.0-14-generic linux-image-extra-3.13.0-19-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 84.6 kB of archives.
After this operation, 423 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ utopic/universe lm-sensors amd64 1:3.3.4-2ubuntu1 [84.6 kB]
Fetched 84.6 kB in 0s (172 kB/s)    
Selecting previously unselected package lm-sensors.
(Reading database ... 291798 files and directories currently installed.)
Preparing to unpack .../lm-sensors_1%3a3.3.4-2ubuntu1_amd64.deb ...
Unpacking lm-sensors (1:3.3.4-2ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up lm-sensors (1:3.3.4-2ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ventrical@ventrical-desktop:~$ 

```

but I'll keep an eye on it.

---

### Post by slickymaster on 2014-04-24
It could well have been some temporary glitch.

---

### Post by NikTh on 2014-04-25
> **slickymaster said:**
> It could well have been some temporary glitch.

Yes. I guess lot of these "temporary glitches" will come in future. Almost always I've had such glitches in development branch.

---

### Post by slickymaster on 2014-04-25
Yeah, that's U+1 for you. It's all in a day's work, as expected.

---

### Post by ventrical on 2014-04-25
[s]Another thought was that perhaps it may be the Ubuntu.info file update missing.[/s]

Got it :)

---

### Post by ventrical on 2014-04-25
Got a few bisquits down the pipe.

```


The following packages will be upgraded:
  dpkg gawk kmod libdpkg-perl libkmod2 locales module-init-tools pkg-config
  unity-greeter vim-common vim-tiny

```

---

### Post by ventrical on 2014-04-26
I  did a conversion (i386) on my overclock box using the /devel/ method repository and got the following.

```

Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
cp: cannot stat ‘/lib/modprobe.d/*’: No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.13.0-24-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for dictionaries-common (1.23.2) ...
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-Asus-Overclock:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Utopic Unicorn (development branch)
Release:    14.10
Codename:    utopic
ventrical@ventrical-Asus-Overclock:~$ 

```

but it's working.

---

### Post by slickymaster on 2014-04-27
Vetrical, don't know if you're aware or not, but did you saw this: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1313085](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1313085)

---

### Post by ventrical on 2014-04-28
> **slickymaster said:**
> Vetrical, don't know if you're aware or not, but did you saw this: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1313085](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1313085)

I had shut that machine down last night. It was off yesterday, all day.  I just booted a while ago and I had lost my networking. I booted into recovery mode from GRuB and was able to update/upgrade with no problem and solved kmod issues.However, the network is still down. It says it's running but program will not load pages .. etc.. Tried to edit, delete network connection , re-create.. no network still.

note @ Slicky

 I think I borked this system on my own. I was doing some experiments with mir, unity8, fvwm-crystal and gnome session.

---


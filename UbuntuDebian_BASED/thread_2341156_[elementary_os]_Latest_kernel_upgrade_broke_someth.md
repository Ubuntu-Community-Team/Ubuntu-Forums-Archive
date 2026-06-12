---
title: "[elementary os] Latest kernel upgrade broke something"
date: 2016-10-25
forum: Ubuntu/Debian BASED
---

### Post by john-geroitos on 2016-10-25
Hello dearest ubuntu community. You've been a great help in the past, I hope you will be again!

Today my elementary os came up with an update which I proceeded to install without looking up what it was (yay me). Turns out it was the latest kernel (or so I think: 4.4.0-45) which -seemingly- installed without issues. After 10 minutes I tried installing something else (git) which failed with some error messages regarding the kernel. I restarted, the system loaded, same issue. I spent the best part of the day googling the issue with little success since I know little about the actual problem...

Here's what apt-get upgrade returns:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  dracut-core kpartx linux-headers-4.4.0-38 linux-headers-4.4.0-38-generic linux-image-4.4.0-38-generic linux-image-extra-4.4.0-38-generic python-dbus
  python-httplib2 python-keyring python-launchpadlib python-lazr.restfulclient python-lazr.uri python-oauth python-secretstorage python-wadllib
  python-zope.interface
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  libmysqlclient20:i386 mysql-common youtube-dl
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 1,618 kB of archives.
After this operation, 41.0 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial/main amd64 youtube-dl all 1:2016.10.25-1~webupd8~xenial0 [809 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main amd64 mysql-common all 5.7.16-0ubuntu0.16.04.1 [15.0 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main i386 libmysqlclient20 i386 5.7.16-0ubuntu0.16.04.1 [794 kB]
Fetched 1,618 kB in 2s (597 kB/s)                                               
(Reading database ... 266427 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.7.16-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-common (5.7.16-0ubuntu0.16.04.1) over (5.7.15-0ubuntu0.16.04.1) ...
Preparing to unpack .../libmysqlclient20_5.7.16-0ubuntu0.16.04.1_i386.deb ...
Unpacking libmysqlclient20:i386 (5.7.16-0ubuntu0.16.04.1) over (5.7.15-0ubuntu0.16.04.1) ...
Preparing to unpack .../youtube-dl_1%3a2016.10.25-1~webupd8~xenial0_all.deb ...
Unpacking youtube-dl (1:2016.10.25-1~webupd8~xenial0) over (1:2016.10.21.1-1~webupd8~xenial0) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.4.0-45-generic (4.4.0-45.66) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-45-generic
) points to /boot/initrd.img-4.4.0-45-generic
 (/boot/initrd.img-4.4.0-45-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-45-generic
) points to /boot/vmlinuz-4.4.0-45-generic
 (/boot/vmlinuz-4.4.0-45-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
run-parts: executing /etc/kernel/postinst.d/dracut 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
dracut: Generating /boot/initrd.img-4.4.0-45-generic
dracut: caps: does not work with systemd in the initramfs
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-45-generic /boot/vmlinuz-4.4.0-45-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
/usr/sbin/update-initramfs: 206: /usr/sbin/update-initramfs: cannot create /var/lib/initramfs-tools/4.4.0-45-generic: Directory nonexistent
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-45-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-45-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-45-generic:
 linux-image-extra-4.4.0-45-generic depends on linux-image-4.4.0-45-generic; however:
  Package linux-image-4.4.0-45-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-45-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-45-generic; however:
  Package linux-image-4.4.0-45-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-45-generic; however:
  Package linux-image-extra-4.4.0-45-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     No apport report written because MaxReports is reached already
                                                                                                                   dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.45.48); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up mysql-common (5.7.16-0ubuntu0.16.04.1) ...
Setting up libmysqlclient20:i386 (5.7.16-0ubuntu0.16.04.1) ...
Setting up youtube-dl (1:2016.10.25-1~webupd8~xenial0) ...
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
ls: cannot access '/var/lib/initramfs-tools': No such file or directory
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
/usr/sbin/update-initramfs: 206: /usr/sbin/update-initramfs: cannot create /var/lib/initramfs-tools/4.4.0-45-generic: Directory nonexistent
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Can anyone point me to the right direction so I can at least keep on looking?

---

### Post by aki-to on 2016-10-26
Exactly the same problem on Peppermint 7.

---

### Post by john-geroitos on 2016-10-27
> **aki-to said:**
> Exactly the same problem on Peppermint 7.

Are you low on disk space by any chance?

EDIT: or were you at the time of the upgrade

---

### Post by john-geroitos on 2016-10-27
I solved the problem, or so it seems, apt no longer returns errors. I tried several things so I will try to guide you.

First of all the problem seemed to be with the latest kernel update 4.4.0-45-generic. Before continuing, assuming your installation is bootable, check which kernel you're using:
```
uname -r
```
Mine returned 4.4.0-43-generic

Then find out how many kernels are installed
```
ls -l initrd*
```
This line of code no longer works for me, I'm gonna just assume its ok. Before that it returned 3 kernels:
4.4.0-38-generic
4.4.0-43-generic
4.4.0-45-generic

At some point before the problem first showed up I had initramfs-tools and dracut at the same time, causing a conflict. If you only have one of them, leave it as is.

Just to be sure, I tried installing the kernel my system was using:
```
sudo apt-get install linux-image-4.4.0-42-generic linux-image-extra-4.4.0-42-generic
```

Since your system already loads without errors and everything seems to be working fine, you need to remove leftovers
```
sudo apt-get autoremove
```

The removal script returned a couple of failures regarding missing directories so I created the missing directories, script went on no problem after that.

I will not mark this as solved until someone wiser than me confirms my steps and someone with the same problem tries it.

---


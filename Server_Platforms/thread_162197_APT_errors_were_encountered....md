---
title: "APT: errors were encountered..."
date: 2006-04-18
forum: Server Platforms
---

### Post by limaunion on 2006-04-18
Hi! I recently installed Ubuntu Server Dapper 6.0.6 in a Compaq Proliant DL360 without problems, except for this one. 

I installed cacti (network monitor) and cacti-cactid (poller), the first one was successfully installed but the cacti-cactid package is giving me some problems, for example:

$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libpam-runtime linux-image-686 linux-restricted-modules-686
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up cacti-cactid (0.8.6g-1build1) ...
dpkg: error processing cacti-cactid (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 cacti-cactid
E: Sub-process /usr/bin/dpkg returned an error code (1)

These are my current mounted partitions (for just in case this information is needed):

$ mount | sort
/dev/cciss/c0d0p1 on / type reiserfs (rw,notail)
/dev/cciss/c0d0p2 on /usr type reiserfs (rw,nodev,notail)
/dev/cciss/c0d0p3 on /var type reiserfs (rw,nosuid,nodev,notail)
/dev/cciss/c0d0p5 on /tmp type reiserfs (rw,nosuid,nodev,notail)
/dev/cciss/c0d0p6 on /home type reiserfs (rw,noexec,nosuid,nodev,notail,usrquota)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-19-686/volatile type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
udev on /dev type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
varrun on /var/run type tmpfs (rw)

I've also tried 'apt-get --purge remove cacti-cactid' and reinstall but didn't solve anything.

Any ideas what's going on here ? Thanks in advance.
JC

---

### Post by LordHunter317 on 2006-04-18
The package has a bug in it.  Seeing as dapper isn't formally released yet, this isn't suprising.

You can't do anything besides fix it yourself or wait for an update.

---

### Post by Linuturk on 2007-03-02
This has not been fixed and we are close to Feisty.

---


---
title: "Server: Upgrading 10.04 to 12.04 dpkg error"
date: 2013-03-16
forum: Server Platforms
---

### Post by Big Dan on 2013-03-16
Hello, 

  I'm running Ubuntu 10.04 x64 on a VPS machine. My intent is to use the VPS as my 'work' machine and VNC into it. I'd like to upgrade it to the latest LTS (12.04). With a fresh image in OpenVZ I login as root and run:

```
apt-get update && apt-get upgrade && shutdown -r 0
```

This process goes fine. I then follow the network upgrade instructions here: [https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

Updates download fine when dpkg is running I get the following error

```
The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug in a browser at
http://bugs.launchpad.net/ubuntu/+source/update-manager/+filebug and
attach the files in /var/log/dist-upgrade/ to the bug report.
installArchives() failed

dpkg: dependency problems prevent configuration of libnih-dbus1:
 libnih-dbus1 depends on libnih1 (= 1.0.3-4ubuntu9.1); however:
  Version of libnih1 on system is 1.0.1-1.
dpkg: error processing libnih-dbus1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnih-dbus1

Upgrade complete

The upgrade has completed but there were errors during the upgrade
process.

```

so I run dpkg --configure -a  and get the following output

```
root@waffles:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of libapt-pkg4.12:
 libapt-pkg4.12 depends on libc6 (>= 2.15); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.12.
 libapt-pkg4.12 depends on libstdc++6 (>= 4.6); however:
  Version of libstdc++6 on system is 4.4.3-4ubuntu5.1.
dpkg: error processing libapt-pkg4.12 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapt-inst1.4:
 libapt-inst1.4 depends on libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.10); however:
  Package libapt-pkg4.12 is not configured yet.
 libapt-inst1.4 depends on libc6 (>= 2.14); however:
  Version of libc6 on system is 2.11.1-0ubuntu7.12.
dpkg: error processing libapt-inst1.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnih-dbus1:
 libnih-dbus1 depends on libnih1 (= 1.0.3-4ubuntu9.1); however:
  Version of libnih1 on system is 1.0.1-1.
dpkg: error processing libnih-dbus1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapt-pkg4.12
 libapt-inst1.4
 libnih-dbus1

```

I'm no command line ninja -- any idea here? 

Thanks, 
Dan

---

### Post by chrisguk on 2013-03-16
Hi immediately after you receive that error did you type:

sudo apt-get install -f

This forces the an errors produced by dpkg

---

### Post by schragge on 2013-03-16
Try ```
apt-get dist-upgrade
```

---

### Post by Big Dan on 2013-03-17
> **chrisguk said:**
> Hi immediately after you receive that error did you type:

sudo apt-get install -f

This forces the an errors produced by dpkg

Hi Chris, 

  Thanks for the reply. I forgot to mention I have run apt-get install -f and this error is produced

```
root@waffles:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libnih1
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libnih1
2 upgraded, 0 newly installed, 0 to remove and 273 not upgraded.
1 not fully installed or removed.
Need to get 0B/4707kB of archives.
After this operation, 230kB of additional disk space will be used.
Do you want to continue [Y/n]?
locale: /lib/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Preconfiguring packages ...
(Reading database ... 21926 files and directories currently installed.)
Preparing to replace libc6 2.11.1-0ubuntu7.12 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
locale: /lib/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
WARNING: init script for samba not found.
Stopping some services possibly affected by the upgrade (will be restarted later):
  cron: stopping...done.

WARNING: this version of the GNU libc requires kernel version
2.6.24 or later. Please upgrade your kernel before installing
glibc.

The installation of a 2.6 kernel _could_ ask you to install a new libc
first, this is NOT a bug, and should *NOT* be reported. In that case,
please add lenny sources to your /etc/apt/sources.list and run:
  apt-get install -t lenny linux-image-2.6
Then reboot into this new kernel, and proceed with your upgrade
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't get where I'm supposed to get lenny sources from (I'm assuming Debian) but it makes no sense that the kernel isn't updated as part of the upgrade process. I even restarted after the error thinking I would switch the new kernel with a reboot. 
> **schragge said:**
> Try ```
apt-get dist-upgrade
```

I've tried this too it results in 0 updates found.

---


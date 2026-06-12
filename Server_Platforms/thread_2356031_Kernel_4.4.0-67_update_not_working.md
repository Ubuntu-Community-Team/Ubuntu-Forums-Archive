---
title: "Kernel 4.4.0-67 update not working"
date: 2017-03-19
forum: Server Platforms
---

### Post by fishman444 on 2017-03-19
Apologies if this has already been asked, but I couldn't see it anywhere.

About 3 days ago I ran 'apt update' on my production KVM host just before going to bed and saw that kernel version 4.4.0-67 was available, so I upgraded that host and all of its VM's using 'apt dist-upgrade' and 'apt autoremove' as I have always done. The new kernel image was installed, rebooted, everything seemed normal. I later saw [https://www.ubuntu.com/usn/usn-3234-1/](https://www.ubuntu.com/usn/usn-3234-1/) which explained what the upgrade was for. All seemed well.

All of this is on Ubuntu Server 16.04.2 amd64 running on Xeon E5-2630 v3 hardware.

Now today I am installing a new machine at home and for various reasons related to cabling could not attach it to the network during install. I installed it from a usb stick containing the 16.04.2 ISO and then later ran

```

root@host4:~# apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Fetched 306 kB in 0s (986 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
40 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@host4:~# apt list --upgradable
Listing... Done
bind9-host/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
dnsutils/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
grub-common/xenial-updates 2.02~beta2-36ubuntu3.8 amd64 [upgradable from: 2.02~beta2-36ubuntu3.7]
grub-efi-amd64/xenial-updates 2.02~beta2-36ubuntu3.8 amd64 [upgradable from: 2.02~beta2-36ubuntu3.7]
grub-efi-amd64-bin/xenial-updates 2.02~beta2-36ubuntu3.8 amd64 [upgradable from: 2.02~beta2-36ubuntu3.7]
grub-efi-amd64-signed/xenial-updates 1.66.8+2.02~beta2-36ubuntu3.8 amd64 [upgradable from: 1.66.7+2.02~beta2-36ubuntu3.7]
grub-legacy-ec2/xenial-updates,xenial-updates 0.7.9-48-g1c795b9-0ubuntu1~16.04.1 all [upgradable from: 0.7.8-49-g9e904bb-0ubuntu1~16.04.4]
grub2-common/xenial-updates 2.02~beta2-36ubuntu3.8 amd64 [upgradable from: 2.02~beta2-36ubuntu3.7]
init/xenial-updates 1.29ubuntu4 amd64 [upgradable from: 1.29ubuntu3]
init-system-helpers/xenial-updates,xenial-updates 1.29ubuntu4 all [upgradable from: 1.29ubuntu3]
libbind9-140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libdns-export162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libdns162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libevent-2.0-5/xenial-updates,xenial-security 2.0.21-stable-2ubuntu0.16.04.1 amd64 [upgradable from: 2.0.21-stable-2]
libicu55/xenial-updates,xenial-security 55.1-7ubuntu0.1 amd64 [upgradable from: 55.1-7]
libisc-export160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libisc160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libisccc140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libisccfg140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
liblwres141/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.5 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.4]
libspice-server1/xenial-updates,xenial-security 0.12.6-4ubuntu0.2 amd64 [upgradable from: 0.12.6-4ubuntu0.1]
libvirt-bin/xenial-updates 1.3.1-1ubuntu10.8 amd64 [upgradable from: 1.3.1-1ubuntu10.7]
libvirt0/xenial-updates 1.3.1-1ubuntu10.8 amd64 [upgradable from: 1.3.1-1ubuntu10.7]
libxml2/xenial-updates,xenial-security 2.9.3+dfsg1-1ubuntu0.2 amd64 [upgradable from: 2.9.3+dfsg1-1ubuntu0.1]
libxml2-utils/xenial-updates,xenial-security 2.9.3+dfsg1-1ubuntu0.2 amd64 [upgradable from: 2.9.3+dfsg1-1ubuntu0.1]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.66.70 amd64 [upgradable from: 4.4.0.62.65]
linux-signed-generic/xenial-updates,xenial-security 4.4.0.66.70 amd64 [upgradable from: 4.4.0.62.65]
linux-signed-image-generic/xenial-updates,xenial-security 4.4.0.66.70 amd64 [upgradable from: 4.4.0.62.65]
mdadm/xenial-updates 3.3-2ubuntu7.2 amd64 [upgradable from: 3.3-2ubuntu7.1]
nano/xenial-updates 2.5.3-2ubuntu2 amd64 [upgradable from: 2.5.3-2ubuntu1]
qemu-block-extra/xenial-updates 1:2.5+dfsg-5ubuntu10.9 amd64 [upgradable from: 1:2.5+dfsg-5ubuntu10.8]
qemu-kvm/xenial-updates 1:2.5+dfsg-5ubuntu10.9 amd64 [upgradable from: 1:2.5+dfsg-5ubuntu10.8]
qemu-system-common/xenial-updates 1:2.5+dfsg-5ubuntu10.9 amd64 [upgradable from: 1:2.5+dfsg-5ubuntu10.8]
qemu-system-x86/xenial-updates 1:2.5+dfsg-5ubuntu10.9 amd64 [upgradable from: 1:2.5+dfsg-5ubuntu10.8]
qemu-utils/xenial-updates 1:2.5+dfsg-5ubuntu10.9 amd64 [upgradable from: 1:2.5+dfsg-5ubuntu10.8]
resolvconf/xenial-updates,xenial-updates 1.78ubuntu4 all [upgradable from: 1.78ubuntu2]
snap-confine/xenial-updates 2.22.6 amd64 [upgradable from: 2.21]
snapd/xenial-updates 2.22.6 amd64 [upgradable from: 2.21]
tcpdump/xenial-updates,xenial-security 4.9.0-1ubuntu1~ubuntu16.04.1 amd64 [upgradable from: 4.7.4-1ubuntu1]
ubuntu-core-launcher/xenial-updates 2.22.6 amd64 [upgradable from: 2.21]
root@host4:~#

```

All of this looks reasonable except that the 3 kernel packages seem to have rolled back to 4.4.0.66. I have since started up a long-disused VM on another host and the same thing is happening.

On the production machine, which is running 4.4.0.67 I have done the following:

```

root@host2:~# uname -a
Linux host2 4.4.0-67-generic #88-Ubuntu SMP Wed Mar 8 16:34:45 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
root@host2:~# apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 306 kB in 0s (642 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
root@host2:~# apt show linux-generic
Package: linux-generic
Version: 4.4.0.66.70
Priority: optional
Section: kernel
Source: linux-meta
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 12.3 kB
Depends: linux-image-generic (= 4.4.0.66.70), linux-headers-generic (= 4.4.0.66.70)
Supported: 5y
Download-Size: 1,784 B
APT-Sources: http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: Complete Generic Linux kernel and headers
 This package will always depend on the latest complete generic Linux kernel
 and headers.


N: There is 1 additional record. Please use the '-a' switch to see it
root@host2:~#



```

So the 4.4.0-67 kernel seems to have disappeared and the repository only has 4.4.0-66, which is still the subject of a security notice on the USN site. The production machine is in a rack in a datacenter so is unlikely to have anyone trying to log into it, but I would prefer not to be running it with a known broken kernel.

Does anyone know if the 4.4.0.67 kernel has been rolled back and if so should I do anything about it on my production server? Or is this a problem with apt? I have spent a couple of hours searching for any news on this and haven't found anything.

Many thanks

John

---

### Post by jeremy31 on 2017-03-19
Check ```
apt search linux-image-4.4.0.67
```
They may have pushed it to the security and update repos by mistake instead of proposed, which is where it appears to be now

---

### Post by Doug S on 2017-03-19
> **fishman444 said:**
> Does anyone know if the 4.4.0.67 kernel has been rolled back and if so should I do anything about it on my production server? Or is this a problem with apt? I have spent a couple of hours searching for any news on this and haven't found anything.I think whatever is going on with kernel 4.4.0.67 is the same or similar to what is going on with kernel 4.8.0-42, and the issue is that there doesn't seem to be any definitive / authoritative statement as to exactly what happened (I've spent hours searching about it also). There are several posts about it.

On one of my 16.04 servers, I do not have it installed, and I get this for Jeremy's suggested command:
```
doug@DOUG-64:~$ apt search linux-image-4.4.0.67
Sorting... Done
Full Text Search... Done
linux-image-4.4.0-67-generic/xenial-updates,xenial-security 4.4.0-67.88 amd64
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP

linux-image-4.4.0-67-lowlatency/xenial-updates,xenial-security 4.4.0-67.88 amd64
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP

```But get this for updates:
```
$ sudo apt update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://ca.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Fetched 306 kB in 2s (127 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

```  
For another 16.04 server, that does have it installed, I get:
```
$ apt search linux-image-4.4.0.67
Sorting... Done
Full Text Search... Done
linux-image-4.4.0-67-generic/xenial-updates,xenial-security,now 4.4.0-67.88 amd64 [installed,automatic]
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP

linux-image-4.4.0-67-lowlatency/xenial-updates,xenial-security 4.4.0-67.88 amd64
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP

```And on a 16.10 desktop, without 4.8.0-42 installed, I get:
```
$ apt search linux-image-4.8.0.42
Sorting... Done
Full Text Search... Done
linux-image-4.8.0-42-generic/yakkety-updates 4.8.0-42.45 amd64
  Linux kernel image for version 4.8.0 on 64 bit x86 SMP

linux-image-4.8.0-42-lowlatency/yakkety-updates 4.8.0-42.45 amd64
  Linux kernel image for version 4.8.0 on 64 bit x86 SMP

```but also "All packages are up to date."

---

### Post by pelm on 2017-03-20
The same on my Ubuntu desktop 16.04 running kernel 4.4.0-66. The new 67-kernel is listed in the repository but isn't updating. What is going on? Can't find any information neither.

```
$ apt search linux-image-4.4.0.67
Sorting... Done
Full Text Search... Done
linux-image-4.4.0-67-generic/xenial-updates,xenial-security 4.4.0-67.88 amd64
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP

linux-image-4.4.0-67-lowlatency/xenial-updates,xenial-security 4.4.0-67.88 amd64
  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
```

---

### Post by Bashing-om on 2017-03-20
et all;

Phased updates ??
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)
[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

So far as I am aware TimeBasedReleases are still in effect .
However, one can over-ride the system;
```

sudo apt update
sudo apt full-upgrade

```
I would expect to pull in the held back kernel .

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by fishman444 on 2017-03-21
Thanks for all the repsonses so far. Doug's message about the 4.8 series is interesting and I should have said that I have seen the same behaviour with some VM's I have that use the HWE kernel (I don't use 16.10).

I shall keep watching to see if anything changes.

---


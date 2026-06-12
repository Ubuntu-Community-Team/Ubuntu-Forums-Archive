---
title: "hostname change does not persist reboot in 18.04."
date: 2018-04-30
forum: Server Platforms
---

### Post by d-h-s on 2018-04-30
Hi,

I recently installed several Ubuntu 18.04. VMs (as a server, without any GUI), two of which where identical regarding all the specs (CPU, RAM, disk).
To save me some work I installed one of the two VMs and then cloned it. 

But after changing the hostname in /etc/hosts and /etc/hostname on VM2 (lets call it host2), this does only change the hostname while the VM is running. After a reboot the hostname is switched back to 'host1'.

I also tried 'dpkg-reconfigure hostname' - without any success - and grepped  /etc for 'host1', but did not found anything.


Does anybody know how I can change the hostname so it persists?
I don't mind technical answers.

---

### Post by LHammonds on 2018-04-30
I'm installing the release version of 18.04 using the alternative installer (so I can use LVM).  I will install it with a generic server name and switch it to a new name after install to see if I witness the same issue.

I'll update this post and let you know my findings.

**EDIT:** The name change remains permanent for me.

Host: ESXi 6.0.0
Server ISO Image: ubuntu-18.04-server-amd64.iso
Release: 18.04
Codename: bionic
Kernel: 4.15.0-20-generic

Exact steps I performed to change the name from "srv-ubuntu" to "srv-mariadb" which was immediately after the initial login.


[list=1]
[*]sudo vi /etc/hosts
Change from:
```
127.0.1.1 srv-ubuntu
```
Change to:
```
127.0.1.1 srv-mariadb
```
[*]sudo vi /etc/hostname
Change from:
```
srv-ubuntu
```
Change to:
```
srv-mariadb
```
[*]reboot
[/list]


LHammonds

---

### Post by d-h-s on 2018-05-01
Thanks, but I already tried this and it does not work. Strangely, other distros, like Debian, accept this way of changing the hostname.
I also regenerated all SSH host keys, in case Ubuntu would parse the '@hostX' part of the public keys. But to no avail.

Anyways, I did a clean install from the most current 18.04. server live iso, and the problem is still the same.

But I noticed something weird in syslog:
After cloning the VM and changing the hostname from 'ubuntu1' to 'ubuntu2', the second VM has the correct hostname during boot:

 ```
May 01 11:11:09 ubuntu2 kernel: Linux version 4.15.0-20-generic (buildd@lgw01-amd64-039) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 20
```

This carries on through the init, until shortly before network initialization and cloud-init:

```
May 01 11:11:10 ubuntu2 kernel: audit: type=1400 audit(1525173070.068:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/lxc-start" pid=599 coMay 01 11:11:10 ubuntu2 audit[598]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4486/usr/lib/snapd/snap-confine" pid=598 comm="apparmo
May 01 11:11:10 ubuntu2 audit[598]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4486/usr/lib/snapd/snap-confine//mount-namespace-captu
May 01 11:11:10 ubuntu2 audit[600]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=600 comm="apparmor_parser"
May 01 11:11:10 ubuntu2 audit[600]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=600 comm="apparmor_parser"
May 01 11:11:10 **ubuntu2** audit[600]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=600 comm="apparmor_parser"
May 01 11:11:10 **ubuntu1** apparmor[529]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
May 01 11:11:10 ubuntu1 audit[602]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=602 comm="apparmor_parser"
May 01 11:11:10 ubuntu1 audit[602]: AVC apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=
May 01 11:11:10 ubuntu1 cloud-init[394]: Cloud-init v. 18.2 running 'init-local' at Tue, 01 May 2018 11:11:09 +0000. Up 4.05 seconds.
```

so, at some point during init there must be something which triggers the hostname to go back to its original one.

I even unpacked the initrd but did not found anything pointing to why the hostname change does happen.

I'm really clueless here.



Here's the information on my setup:

Host: Debian 9, using kvm and libvirt
Image: ubuntu-18.04-live-server-amd64.iso
VM Kernel: 4.15.0-20-generic

---

### Post by LHammonds on 2018-05-01
One difference between us is the "live" vs the "alternate" ISO image.

---

### Post by d-h-s on 2018-05-01
I'll be damned... Using the alternate net install image as a base the hostname change does persist.

Still, why does that "Live Server" Installer generate such a mess? 


Anyways, much thanks for helping, LHammonds!

---

### Post by LHammonds on 2018-05-01
I have no idea why the "live" CD exists.  I started to use it but noticed there was no way to configure LVM so it is useless to me...thus I don't know what other peculiarities there are with it.  It is apparently more than just installer differences it seems.

LHammonds

---

### Post by bluexmas on 2018-05-02
This is disturbing, there are configuration differences between "live" and "alternate".

On "live" iso you need to edit "/etc/cloud/cloud.cfg" and change "preserve_hostname" to "true". After this change I see the hostname is persistent.

This config file doesn't exists on "alternate" iso. I think it's related to some cloud deployment package configuration.


The big question is which iso will we deploy on VMs? Because the configs and services look different between the two.

PS: Another difference, there's a mount called:

> /dev/loop0         88704   88704         0 100% /snap/core/4486

on the "live" iso install. I think some "snaps" package is installed by default, used to manage deployments or services or whatever.

---

### Post by LHammonds on 2018-05-02
The [Ubuntu 18.04 Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") do not identify anything specific about the differences between the live and alternative CDs other than this one lonely statement:

> The next generation Subiquity server installer, brings the comfortable live session and speedy install of Ubuntu Desktop to server users at last.

N.B., If you require LVM, RAID, multipath, vlans, bonds, or the ability to re-using existing partitions, you will want to continue to use the alternate installer which can be downloaded from [http://cdimage.ubuntu.com/releases/18.04/release/](http://cdimage.ubuntu.com/releases/18.04/release/)

Funny that those reasons for the "alternative" seem to be a main requirement of server (to me).  But there are definite differences between the two other than the installer.  You don't end up with the exact same server if you pick the same choices in both.

I cannot find anything on the net about those exact differences in terms of what they are, if they are just packaging mistakes and will be corrected later.  I opened [another thread for this discussion](https://ubuntuforums.org/showthread.php?t=2390785).

LHammonds

---

### Post by balajit-kubendran on 2018-08-24
> **LHammonds said:**
> The [Ubuntu 18.04 Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") do not identify anything specific about the differences between the live and alternative CDs other than this one lonely statement:



Funny that those reasons for the "alternative" seem to be a main requirement of server (to me).  But there are definite differences between the two other than the installer.  You don't end up with the exact same server if you pick the same choices in both.

I cannot find anything on the net about those exact differences in terms of what they are, if they are just packaging mistakes and will be corrected later.  I opened [another thread for this discussion]("https://ubuntuforums.org/showthread.php?t=2390785").

LHammonds



Yes i see same issue with my multiple box after cloning on VMware 6.0, either user hostnamectl or manual edit of /etc/hostname. after reboot it restores to old value.

---

### Post by LHammonds on 2018-08-25
> **balajit-kubendran said:**
> Yes i see same issue with my multiple box after cloning on VMware 6.0, either user hostnamectl or manual edit of /etc/hostname. after reboot it restores to old value.
I mentioned a workaround solution for this in the [other thread](https://ubuntuforums.org/showthread.php?t=2390785) which I used to track the differences between LIVE and ALTERNATIVE.

LHammonds

---

### Post by realruntime on 2019-02-14
> **LHammonds said:**
> I mentioned a workaround solution for this in the [other thread](https://ubuntuforums.org/showthread.php?t=2390785) which I used to track the differences between LIVE and ALTERNATIVE.

LHammonds

Thanks for that! 

What sh**t is this all about? What ever reason can you have to *not* preserve the hostname on a Linux server???

---


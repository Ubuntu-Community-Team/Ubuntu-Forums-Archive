---
title: "Samba dependencies broken in 22.04"
date: 2022-02-06
forum: Ubuntu Development Version
---

### Post by moroninorin on 2022-02-06
Hi
After upgrading from 20.04 to 22.04 samba was removed and can not be installed due to incorrectly defined dependencies 

The following packages have unmet dependencies:
 samba : Depends: python3-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.13.14+dfsg-0ubuntu2) but it is not going to be installed
         Depends: libwbclient0 (= 2:4.13.14+dfsg-0ubuntu2) but 2:4.13.17~dfsg-0ubuntu0.21.04.1 is to be installed
         Depends: samba-libs (= 2:4.13.14+dfsg-0ubuntu2) but it is not going to be installed
         Recommends: python3-markdown but it is not going to be installed
         Recommends: samba-dsdb-modules but it is not going to be installed
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Dependecy for libwbclient0 is equal to 2:4.13.14+dfsg-0ubuntu2 and not equal or higher than

apt-get install libwbclient0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libwbclient0 is already the newest version (2:4.13.17~dfsg-0ubuntu0.21.04.1).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I considered removing libwbclient0 to allow installation of samba to pick decisered version but would not like to break freeradius that is also depending on the same library

apt-get remove libwbclient0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freeradius-common freeradius-config freeradius-utils freetds-common libct4 libfreeradius3
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  cifs-utils freeradius freeradius-krb5 libwbclient0
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 3,503 kB disk space will be freed.
Do you want to continue? [Y/n] n

Please help resolve the issue that does not require building samba from source

/Regards
Moroni

---

### Post by howefield on 2022-02-06
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by Smask on 2022-02-06
The only thing at the moment that I can see is perl 5.32 -> 5.34 wants to unload 168 packages, but no mentions of samba.

I have proposed enabled.

---

### Post by deadflowr on 2022-02-06
Your libwbclient0 is wrong version for 22.04.
(feels odd to state that as you probably already know that, 
but it's the only package in which we do know which version is currently installed on your system)

What are your current sources?
What does 
```
sudo apt update
``` output?

---

### Post by moroninorin on 2022-02-06
apt update
Hit:1 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done

Well there are no "newer" version for libwbclient0 and I have for some reason packages that been kept back.
apt-get upgrade libwbclient0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libwbclient0 is already the newest version (2:4.13.17~dfsg-0ubuntu0.21.04.1).
Calculating upgrade... Done
The following packages have been kept back:
  gcc-10-base gcc-10-base:i386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Where do you see its the wrong version for 22.04 ?

I would think that when upgrading from 20.04 to 22.04 the libwbclient0 should be upgraded to the one provided by 22.04.

/MN

---

### Post by deadflowr on 2022-02-07
I see the issue.
Samba on 20.04 recently got a security update which bumped it up to 2.4.13.17
Samba on 22.04 is still in development and has not receive the security update,
since the security repository channels are usually not open for the development release until late in the development cycle.
So it's version is stuck at the lower 2.4.13.14 for now, or until they update it to a newer version.

The development cycle is in constant flux with many moving parts, so it sometimes takes a moment (or longer) for things to move in and out of the repositories.

Personally, I would simply remove samba and then reinstall it, which will pull in the 22.04 version.
That seems like it would be the quickest course of action.

You can also file a bug report on the issue in the hopes that it pushes toward an update quicker.
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by rew82 on 2022-02-07
Just checking that Samba should be okay with a fresh install of 22.04? I'm wanting to help test next version but I rely on Samba to access my home server (Ubuntu server 20.04). Anyone see any problem with this?

---

### Post by moroninorin on 2022-02-08
Hi
Samba was already uninstalled by the upgrade process.
I have simply not been able to re-install it.

For some reason I was not informat that the samba would be affected when doing the upgrade or I missed that information.

If I would remove libwbclient0 it would affect other software depending on that as well.
Unsure what the dependencies for freeradius are but do not want to break other things in the process.

apt-get remove libwbclient0
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  freeradius-common freeradius-config freeradius-utils freetds-common libct4 libfreeradius3
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  cifs-utils freeradius freeradius-krb5 libwbclient0
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
After this operation, 3,503 kB disk space will be freed.


For now as a work around I have simply compiled samba from source.

samba -b
Samba version: 4.15.5
Build environment:
Paths:
   BINDIR: /usr/bin
   SBINDIR: /usr/sbin
   CONFIGFILE: /usr/local/samba/etc/smb.conf
   NCALRPCDIR: /usr/local/samba/var/run/ncalrpc
   LOGFILEBASE: /usr/local/samba/var
   LMHOSTSFILE: /usr/local/samba/etc/lmhosts
   DATADIR: /usr/local/samba/share
   MODULESDIR: /usr/local/samba/lib
   LOCKDIR: /usr/local/samba/var/lock
   STATEDIR: /var/lib/samba
   CACHEDIR: /usr/local/samba/var/cache
   PIDDIR: /usr/local/samba/var/run
   PRIVATE_DIR: /var/lib/samba/private
   CODEPAGEDIR: /usr/local/samba/share/codepages
   SETUPDIR: /usr/local/samba/share/setup
   WINBINDD_SOCKET_DIR: /usr/local/samba/var/run/winbindd
   NTP_SIGND_SOCKET_DIR: /usr/local/samba/var/lib/ntp_signd

---

### Post by Claus7 on 2022-02-08
Hello,

just to add what I see when clicking on samba under synaptic:
> samba:

Package samba has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

Regards!

---

### Post by moroninorin on 2022-02-09
Hi
Not sure what that exactly means :o

Just noticed that I should have run the update-manager with -p and not -d

Maybe I should have paid more attention :lolflag:

[https://itsubuntu.com/how-to-upgrade-ubuntu-22-04-lts/](https://itsubuntu.com/how-to-upgrade-ubuntu-22-04-lts/)

I was thinking is 22 04 already released and -d is for devel-release and -p for proposed :(

Maybe just as good. When is 22.04 plan to be released anyway :popcorn:

So one would not have to upgrade twice :P
The development version should still allow users to upgrade samba so still some issue.
Better finding out issues before releasing :o

What would be required to file a "bug" since I usually do not file any bug reports :(

Everything except for the samba seem to be working sort of as expected.

---


---
title: "ACL Support"
date: 2005-12-02
forum: Server Platforms
---

### Post by mike4ubuntu on 2005-12-02
How do you turn on ACL support in Ubuntu Breezy?

I tried installing, but got errors:

$ sudo apt-get install acl
...
Reading package lists... Done
Building dependency tree... Done
Package acl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
...
E: Package acl has no installation candidate
----
I think there is also something that needs to be done with mounting partitions with acl support.

---

### Post by grendelkhan on 2005-12-02
try installing libacl1

if you're using ext3 you do need to add mount flags, but if you're using xfs or jfs, you don't.

---

### Post by TeeSeeJay on 2005-12-02
I'd suggest checking your /etc/apt/sources.list (post your contents here if you're unsure what you're looking at).

Do an "apt-get update" after checking sources.list and try again.

There is an "acl" option you must include in your mount command to enable ACLs on that volume.

---

### Post by mike4ubuntu on 2005-12-02
I'm not sure what needs to be in the /etc/apt/sources.list other that what's put there by default:

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Fri Dec  2 09:52:09 2005 from 70.88.226.225
mike@lic4:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by mike4ubuntu on 2005-12-02
looks like apt-get update did the trick, thanks.

$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release [30.9kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [586kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources [914kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [15.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [5785B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [8552B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 4144kB in 19s (216kB/s)
Reading package lists... Done

$ sudo apt-get install acl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  acl
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 46.7kB of archives.
After unpacking 188kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe acl 2.2.29-1 [46.7kB]
Fetched 46.7kB in 3s (14.9kB/s)

Preconfiguring packages ...
Selecting previously deselected package acl.
(Reading database ... 59157 files and directories currently installed.)
Unpacking acl (from .../archives/acl_2.2.29-1_i386.deb) ...
Setting up acl (2.2.29-1) ...

---


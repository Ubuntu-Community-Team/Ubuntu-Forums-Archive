---
title: "Does the new sudo package look suspicious to anyone else?"
date: 2014-03-13
forum: Server Platforms
---

### Post by ouch67 on 2014-03-13
I just did an apt-get upgrade and it want's to download a new sudo package. But the thing is it's the same version as the one I have according to dpkg.

Commands used:

```
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 388 kB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]?


:~$ sudo dpkg -l | grep sudo
ii  sudo                                1.8.6p3-0ubuntu3                           amd64        Provide limited super user privileges to specific users

:~$ sudo apt-cache show sudo
Package: sudo
Priority: important
Section: admin
Installed-Size: 1256
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bdale Garbee <bdale@gag.com>
Architecture: amd64
Version: 1.8.6p3-0ubuntu3.1
Replaces: sudo-ldap
Depends: libc6 (>= 2.15), libpam0g (>= 0.99.7.1), libselinux1 (>= 1.32), libpam-modules
Conflicts: sudo-ldap
Filename: pool/main/s/sudo/sudo_1.8.6p3-0ubuntu3.1_amd64.deb
Size: 387760
MD5sum: 419a5d952898a2e6d97ef3b54a08d1ab
SHA1: 8bc261102208abd1a1d798cdcd35582493fab864
SHA256: d508ed311ee2ea155c78cb1e52b05aa3656fd4e2f7e3b1dd756b6fd4180f608b
Description-en: Provide limited super user privileges to specific users
 Sudo is a program designed to allow a sysadmin to give limited root
 privileges to users and log root activity.  The basic philosophy is to give
 as few privileges as possible but still allow people to get their work done.
 .
 This version is built with minimal shared library dependencies, use the
 sudo-ldap package instead if you need LDAP support for sudoers.
Description-md5: acd82d558698567df941afe9b1ac35df
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: minimal

Package: sudo
Priority: important
Section: admin
Installed-Size: 1244
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Bdale Garbee <bdale@gag.com>
Architecture: amd64
Version: 1.8.6p3-0ubuntu3
Replaces: sudo-ldap
Depends: libc6 (>= 2.15), libpam0g (>= 0.99.7.1), libselinux1 (>= 1.32), libpam-modules
Conflicts: sudo-ldap
Filename: pool/main/s/sudo/sudo_1.8.6p3-0ubuntu3_amd64.deb
Size: 391228
MD5sum: 9d51591e0793dd0115fa1c578d7a6380
SHA1: 501df98a5e62936ab26721c32d4ecce64b0ab70b
SHA256: b836c99a35cfb48b424c837f2827dc34a451b647cf987167f88091ce4de0c2b8
Description-en: Provide limited super user privileges to specific users
 Sudo is a program designed to allow a sysadmin to give limited root
 privileges to users and log root activity.  The basic philosophy is to give
 as few privileges as possible but still allow people to get their work done.
 .
 This version is built with minimal shared library dependencies, use the
 sudo-ldap package instead if you need LDAP support for sudoers.
Description-md5: acd82d558698567df941afe9b1ac35df
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: minimal

:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy

```

Also note how apt-cache shows 2 sudo packages.

Does this look strange to anyone else?

---

### Post by mJayk on 2014-03-13
Indeed, I found your post after a google after wondering the same thing.

---

### Post by CharlesA on 2014-03-13
It's a newer version of sudo 3.1 not 3.0. Just install it and be on your way.

---

### Post by Dave_L on 2014-03-13
Here's the change log, if you're interested in the details:
[http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.8.6p3-0ubuntu3.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/sudo/sudo_1.8.6p3-0ubuntu3.1/changelog)

---

### Post by ouch67 on 2014-03-14
ok, thanks folks

---


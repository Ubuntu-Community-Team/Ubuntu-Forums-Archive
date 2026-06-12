---
title: "Dansguardian"
date: 2007-03-18
forum: Ubuntu Christian Edition
---

### Post by Rory from the Rock on 2007-03-18
Hello everyone.

I am making up a computer with ubuntu on it.  I have been installing educational apps and children's games, I also wish to add dansguardian to the list.  I tried to install it using apt-get from the terminal. 

Here is the info that came up when it tried to install itself.


rheal@rheal-desktop:~$ sudo apt-get install dansguardian
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  clamav clamav-base clamav-freshclam libclamav1 libesmtp5 libssl0.9.7
Suggested packages:
  unrar lha clamav-docs squid
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam dansguardian libclamav1 libesmtp5
  libssl0.9.7
0 upgraded, 7 newly installed, 0 to remove and 226 not upgraded.
Need to get 8913kB of archives.
After unpacking, 14.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe libssl0.9.7 0.9.7g-5ub untu1.1 [2178kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe libclamav1 0.88.4-1 ubuntu1~dapper1 [264kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe libclamav1 0.88.4-1ub untu1~dapper1
  Error reading from server. Remote end closed connection
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe clamav-base 0.88.4- 1ubuntu1~dapper1 [176kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe clamav-base 0.88.4-1u buntu1~dapper1
  Connection timed out
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe clamav-freshclam 0. 88.4-1ubuntu1~dapper1 [5911kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe clamav 0.88.4-1ubun tu1~dapper1 [65.9kB]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe libesmtp5 1.0.3-1 [51.9kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe dansguardian 2.8.0.6-antiviru s-6.3.8-1-1 [267kB]
Fetched 8474kB in 1h28m34s (1595B/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/clamav/libcl](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/clamav/libcl) amav1_0.88.4-1ubuntu1~dapper1_i386.deb Error reading from server. Remote end clo sed connection
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/clamav/clama](http://ca.archive.ubuntu.com/ubuntu/pool/universe/c/clamav/clama) v-base_0.88.4-1ubuntu1~dapper1_all.deb Connection timed out
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-mi ssing.
rheal@rheal-desktop:~$ sudo apt-get install dansguardian
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  clamav clamav-base clamav-freshclam libclamav1 libesmtp5 libssl0.9.7
Suggested packages:
  unrar lha clamav-docs squid
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam dansguardian libclamav1 libesmtp5
  libssl0.9.7
0 upgraded, 7 newly installed, 0 to remove and 226 not upgraded.
Need to get 439kB/8913kB of archives.
After unpacking, 14.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe libclamav1 0.88.4-1 ubuntu1~dapper1 [264kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-backports/universe clamav-base 0.88.4- 1ubuntu1~dapper1 [176kB]
Fetched 273kB in 1m51s (2449B/s)
Preconfiguring packages ...
Selecting previously deselected package libclamav1.
(Reading database ... 84228 files and directories currently installed.)
Unpacking libclamav1 (from .../libclamav1_0.88.4-1ubuntu1~dapper1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.88.4-1ubuntu1~dapper1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.88.4-1ubuntu1~dapper1_i3 86.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.88.4-1ubuntu1~dapper1_i386.deb) ...
Selecting previously deselected package libssl0.9.7.
Unpacking libssl0.9.7 (from .../libssl0.9.7_0.9.7g-5ubuntu1.1_i386.deb) ...
Selecting previously deselected package libesmtp5.
Unpacking libesmtp5 (from .../libesmtp5_1.0.3-1_i386.deb) ...
Selecting previously deselected package dansguardian.
Unpacking dansguardian (from .../dansguardian_2.8.0.6-antivirus-6.3.8-1-1_i386.d eb) ...
Setting up libclamav1 (0.88.4-1ubuntu1~dapper1) ...

Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
Adding system user `clamav'...
Adding new group `clamav' (113).
Adding new user `clamav' (113) with group `clamav'.
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Setting up libssl0.9.7 (0.9.7g-5ubuntu1.1) ...

Setting up libesmtp5 (1.0.3-1) ...

dpkg: dependency problems prevent configuration of dansguardian:
 dansguardian depends on clamav; however:
  Package clamav is not configured yet.
dpkg: error processing dansguardian (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)
rheal@rheal-desktop:~$


I am going to start searching for the answer, based on the errors in configuring clamav,clamav-base,clamav-freshclam and dansguardian.,  But I have dial up and it takes me a long time to dig through to find anything.  So I thought that I would see if any one has seen this before and/or any suggestions.

Thanks...R.

---

### Post by Rory from the Rock on 2007-03-18
Hello again,

I believe that I have found the answer in dansguardian tag-how to install dansguardian.

I will try the configure and re install tomorrow and post results.

If there are other ideas that would be great also.


Thanks...R.

---

### Post by mhancoc7 on 2007-03-18
You could also use the script that we have availble at the Ubuntu CE project site. It will install and configure dansguardian with the GUI that comes with Ubuntu CE.

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/03/popular-packages-edgy.html)

Jereme

---


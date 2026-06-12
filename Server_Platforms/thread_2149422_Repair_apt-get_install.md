---
title: "Repair apt-get install"
date: 2013-05-28
forum: Server Platforms
---

### Post by reynold104 on 2013-05-28
Current server version: 3.2.0-39-generic

Know this issue has been addressed a thousand time but I have read and tried the solutions recommended without success.  My while by /boot was full (but have cleared to 65%) I attempted an apt-get update now I can't install updates or new packages.  Have tried:
apt-get -f install
dpkg --configure -adpkg
apt-get install linux-image-3.2.0-40-generic
dpkg -i linux-server_3.2.0.44.53_amd64.deb

apt-get -o Debug::dpkgProblemResolver=yes dist-upgrade  
apt-get -u dist-upgrade
apt-get clean
apt-get autoclean

current message:
test@ubuntu1:~$ sudo apt-get -f install
[sudo] password for test:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-server
The following packages will be upgraded:
  linux-image-server
1 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,478 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-40-generic; however:
  Package linux-image-3.2.0-40-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.44.53); however:
  Version of linux-image-server on system is 3.2.0.40.48.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
test@ubuntu1:~$

Would appreciate help
Thanks,  Reynold

---


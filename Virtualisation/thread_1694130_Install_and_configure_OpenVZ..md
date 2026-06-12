---
title: "Install and configure OpenVZ."
date: 2011-02-23
forum: Virtualisation
---

### Post by linuxbasiccommand on 2011-02-23
**[1] Install Operation Commands for [OpenVZ.]("http://linuxbasiccommand.blogspot.com/search/label/Virtualization")**
[root@ns ~]# yum -y install vzctrl vzquota vzpkg
Loading "installonlyn" plugin
Loading "fastestmirror" plugin
Setting up Install Process
Setting up repositories
openvz-kernel-rhel5 100% |=========================|  951 B 00:00
openvz-utils 100% |=========================|951 B 00:00
Loading mirror speeds from cached hostfile
Reading repository metadata in from local files
primary.xml.gz 100% |=========================| 31 kB 00:00
openvz-ker: ######################################### 14/14
Added 14 new packages, deleted 0 old in 0.26 seconds
primary.xml.gz 100% |=========================| 5.3 kB 00:00
openvz-uti: ######################################### 21/21
Added 21 new packages, deleted 0 old in 0.13 seconds
Parsing package install arguments
Resolving Dependencies
--> Populating transaction set with selected packages. Please wait.
---> Downloading header for vzpkg to pack into transaction set.
vzpkg-2.7.0-18.noarch.rpm 100% |====================| 4.2 kB 00:00
---> Package vzpkg.noarch 0:2.7.0-18 set to be updated
---> Downloading header for vzquota to pack into transaction set.
vzquota-3.0.9-1.i386.rpm 100% |====================| 3.5 kB 00:00
---> Package vzquota.i386 0:3.0.9-1 set to be updated
--> Running transaction check
--> Processing Dependency: vzyum >= 2.4.0-5 for package: vzpkg
--> Processing Dependency: vzctl >= 2.7.0-23 for package: vzpkg
--> Restarting Dependency Resolution with new changes.
--> Populating transaction set with selected packages. Please wait.
---> Downloading header for vzctl to pack into transaction set.
vzctl-3.0.16-1.i386.rpm 100% |====================| 16 kB 00:00
---> Package vzctl.i386 0:3.0.16-1 set to be updated
---> Downloading header for vzyum to pack into transaction set.
vzyum-2.4.0-11.noarch.rpm 100% |====================| 1ï¼˜ kB 00:00
---> Package vzyum.noarch 0:2.4.0-11 set to be updated
--> Running transaction check
--> Processing Dependency: libvzctl-0.0.2.so for package: vzctl
--> Processing Dependency: vzctl-lib = 3.0.16-1 for package: vzctl
--> Restarting Dependency Resolution with new changes.
--> Populating transaction set with selected packages. Please wait.
---> Downloading header for vzctl-lib to pack into transaction set.
vzctl-lib-3.0.16-1.i386.r 100% |====================| 2.5 kB 00:00
---> Package vzctl-lib.i386 0:3.0.16-1 set to be updated
--> Running transaction check

Dependencies Resolved

===================================================================
Package Arch Version Repository Size
===================================================================
Installing:
  vzpkg noarch 2.7.0-18 openvz-utils 39 k

  vzquota i386 3.0.9-1 openvz-utils 47 k
Installing for dependencies:
  vzctl i386 3.0.16-1 openvz-utils 132 k
  vzctl-lib i386 3.0.16-1 openvz-utils 168 k
  vzyum noarch 2.4.0-11 openvz-utils 361 k
......
More read go to site [Install and configure OpenVZ]("http://linuxbasiccommand.blogspot.com/search/label/Virtualization")

---


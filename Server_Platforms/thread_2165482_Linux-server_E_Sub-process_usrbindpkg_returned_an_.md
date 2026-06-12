---
title: "Linux-server E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-08-05
forum: Server Platforms
---

### Post by Mikog on 2013-08-05
Hello all,

After i did a sudo aptitude safe-upgrade the following errors occurs:

-------------------

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
                Depends: linux-headers-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
E: Unmet dependencies. Try using -f.

-------------------

sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-44-generic linux-headers-3.2.0-44 linux-headers-3.2.0-48 linux-image-3.2.0-48-generic linux-headers-3.2.0-48-generic linux-image-3.2.0-44-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,732 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.48.58); however:
  Version of linux-image-server on system is 3.2.0.51.61.
 linux-server depends on linux-headers-server (= 3.2.0.48.58); however:
  Version of linux-headers-server on system is 3.2.0.51.61.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

------------------------------
sudo dpkg --configure -a
[sudo] password for kerem:
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.48.58); however:
  Version of linux-image-server on system is 3.2.0.51.61.
 linux-server depends on linux-headers-server (= 3.2.0.48.58); however:
  Version of linux-headers-server on system is 3.2.0.51.61.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-server

------------------------------

package list contains the following images:

ii  linux-firmware                                        1.79.6                                                Firmware for Linux kernel drivers
ii  linux-headers-3.2.0-44                                3.2.0-44.69                                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic                        3.2.0-44.69                                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                                3.2.0-48.74                                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic                        3.2.0-48.74                                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-49                                3.2.0-49.75                                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                        3.2.0-49.75                                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-51                                3.2.0-51.77                                           Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic                        3.2.0-51.77                                           Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                                  3.2.0.51.61                                           Linux kernel headers on Server Equipment.
ii  linux-image-3.2.0-44-generic                          3.2.0-44.69                                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic                          3.2.0-48.74                                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                          3.2.0-49.75                                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-51-generic                          3.2.0-51.77                                           Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-server                                    3.2.0.51.61                                           Linux kernel image on Server Equipment.
iU  linux-server                                          3.2.0.48.58                                           Complete Linux kernel on Server Equipment.


---------------
Boot partition is 44% full 
44% /boot

Please advise.

---

### Post by JnPson on 2013-08-05
There is a thread for this in General help. [http://ubuntuforums.org/showthread.php?t=2162203](http://ubuntuforums.org/showthread.php?t=2162203) 

Regards JnPson

---

### Post by ian-weisser on 2013-08-05
> **Mikog said:**
> 
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= [COLOR=#ff0000]3.2.0.48.58[/COLOR]) but [COLOR=#ff0000]3.2.0.51.61[/COLOR] is installed
                Depends: linux-headers-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed

You are telling the system to do something that it considers to be extremely unwise, and it is (properly) refusing.

A bit of research at [https://launchpad.net/ubuntu/precise/amd64/linux-image-server](https://launchpad.net/ubuntu/precise/amd64/linux-image-server) tells us two important clues:

1) linux-image-server **3.2.0.51.61** means that you are running an up-to-date version of Precise (12.04).

2) linux-image-server **3.2.0.48.58** was used in Precise, but was superseded last week by the version you currently have installed. It also tells us that this version used to be in the kernel testing PPA.

This kind of package management error occurs most often due to old PPAs.
Disable your PPAs and third party repositories and try updating again.

---

### Post by Mikog on 2013-08-06
I have looked into my PPA and i dont have any in my directory: /etc/apt/sources.list.d
The directory is stated as empty.
I cant disable anything as there is no PPA present.

It could be that i am looking in the wrong directory?

---

### Post by ian-weisser on 2013-08-06
Also check the file /etc/apt/sources.list. Look for any line that does not include "precise".  grep -v precise /etc/apt/sources.list



Try updating the package list. sudo apt-get update. Post the entire session here.
Then try upgrading again. sudo apt-get upgrade.  Post that entire session, too.

---

### Post by ibjsb4 on 2013-08-06
Something else to give a try ..

```
sudo apt-get clean && sudo apt-get autoremove && sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by ian-weisser on 2013-08-06
[duplicate post removed]

---

### Post by Mikog on 2013-08-07
Hello Ian,

All my sources contain precies:
Output:
----------------
sudo apt-get update

Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release.gpg
Get:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release
Get:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release [49.6 kB]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe TranslationIndex
Get:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Sources [412 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Get:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:7 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Sources [93.1 kB]
Get:8 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:9 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main amd64 Packages [671 kB]
Get:10 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:11 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe amd64 Packages [210 kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [84.9 kB]
Get:13 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:14 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main i386 Packages [692 kB]
Get:15 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:16 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe i386 Packages [214 kB]
Get:17 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Translation-en
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [27.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,383 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [305 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [80.3 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,186 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [320 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [83.3 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,371 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Fetched 3,370 kB in 16s (208 kB/s)
Reading package lists... Done

---------------------

User@server:/etc/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
                Depends: linux-headers-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
E: Unmet dependencies. Try using -f.
---------------

---

### Post by Mikog on 2013-08-07
@IBjsb4

All command output states this error:
----------
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
                Depends: linux-headers-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
E: Unmet dependencies. Try using -f.

---------------
Guys i will be rebooting the server with console access.
Probably the server will hang in the image screen at boot up.

After the reboot i will try the same commands again.
The reboot will properly load the latest image and this might solve my issue.

---

### Post by ibjsb4 on 2013-08-07
I would clean out those old kernels.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Manual](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Manual)

---

### Post by Mikog on 2013-08-10
Gents i did a reboot i came out of the reboot without any issues.
It now has the latest image but an apt-get update and upgrade still gives the same issue.

still gives the error:
-----------------
kerem@sultan:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
                Depends: linux-headers-server (= 3.2.0.48.58) but 3.2.0.51.61 is installed
E: Unmet dependencies. Try using -f.
----------

image 3.2.0.48.58 does not exists on my system any more as i have the latest two images:
These latest two are:
ii  linux-firmware                       1.79.6                               Firmware for Linux kernel drivers
ii  linux-headers-3.2.0-49               3.2.0-49.75                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic       3.2.0-49.75                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-51               3.2.0-51.77                          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic       3.2.0-51.77                          Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                 3.2.0.51.61                          Linux kernel headers on Server Equipment.
ii  linux-image-3.2.0-49-generic         3.2.0-49.75                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-51-generic         3.2.0-51.77                          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-server                   3.2.0.51.61                          Linux kernel image on Server Equipment.
iU  linux-server                         3.2.0.48.58                          Complete Linux kernel on Server Equipment.

---------
Note that the linux server state its release 3.2.0.48.58.. but my system is on image release 3.2.0-51

Issue still remains :(

---


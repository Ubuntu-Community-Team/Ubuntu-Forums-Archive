---
title: "View pending udate command"
date: 2018-03-17
forum: Security
---

### Post by cam17 on 2018-03-17
I was given the command "apt list upgradable" to find pending new updates.  When I logged on via SSH to my Ubuntu Desktop there was 3 packages to be updated? Is the command correct?

Below is the output

buntu 16.04.4 LTS
```
Last login: Thu Mar 15 04:52:53 EDT 2018 from 10.10.10.100 on pts/19
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.13.0-36-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

3 packages can be updated.
0 updates are security updates.

```
```
sudo apt list upgradable
Listing... Done


```

```
sudo apt-get update
Hit:1 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial InRelease
Get:2 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates InRelease [102 kB]
Get:3 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security InRelease [102 kB]
Get:4 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 Packages [742 kB]
Get:5 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main i386 Packages [688 kB]
Get:6 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [317 kB]
Get:7 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main DEP-11 64x64 Icons [226 kB]
Get:8 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/universe amd64 Packages [600 kB]
Get:9 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/universe i386 Packages [555 kB]
Get:10 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [190 kB]
Get:11 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [263 kB]
Get:12 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:13 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/main amd64 Packages [464 kB]      
Get:14 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/main i386 Packages [418 kB]       
Get:15 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/main amd64 DEP-11 Metadata [67.3 kB]
Get:16 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/main DEP-11 64x64 Icons [77.2 kB] 
Get:17 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/universe amd64 Packages [323 kB]  
Get:18 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/universe i386 Packages [282 kB]   
Get:19 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:20 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Fetched 5,560 kB in 9s (578 kB/s)                                                                     
Reading package lists... Done
```

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.13.0-32 linux-headers-4.13.0-32-generic linux-image-4.13.0-32-generic
  linux-image-extra-4.13.0-32-generic linux-signed-image-4.13.0-32-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  dpkg dpkg-dev firefox firefox-locale-en isc-dhcp-client isc-dhcp-common libdpkg-perl
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.4 MB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 dpkg amd64 1.18.4ubuntu1.4 [2,088 kB]
Get:2 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 isc-dhcp-client amd64 4.3.3-5ubuntu12.10 [224 kB]
Get:3 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 isc-dhcp-common amd64 4.3.3-5ubuntu12.10 [105 kB]
Get:4 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 dpkg-dev all 1.18.4ubuntu1.4 [584 kB]
Get:5 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.4 [195 kB]
Get:6 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 firefox amd64 59.0.1+build1-0ubuntu0.16.04.1 [44.5 MB]
Get:7 [http://archive.ubuntu.mirror.rafal.ca/ubuntu](http://archive.ubuntu.mirror.rafal.ca/ubuntu) xenial-updates/main amd64 firefox-locale-en amd64 59.0.1+build1-0ubuntu0.16.04.1 [701 kB]
Fetched 48.4 MB in 1min 16s (629 kB/s)                                                                
(Reading database ... 257489 files and directories currently installed.)
Preparing to unpack .../dpkg_1.18.4ubuntu1.4_amd64.deb ...
Unpacking dpkg (1.18.4ubuntu1.4) over (1.18.4ubuntu1.3) ...
Setting up dpkg (1.18.4ubuntu1.4) ...
Processing triggers for man-db (2.7.5-1) ...
(Reading database ... 257489 files and directories currently installed.)
Preparing to unpack .../isc-dhcp-client_4.3.3-5ubuntu12.10_amd64.deb ...
Unpacking isc-dhcp-client (4.3.3-5ubuntu12.10) over (4.3.3-5ubuntu12.9) ...
Preparing to unpack .../isc-dhcp-common_4.3.3-5ubuntu12.10_amd64.deb ...
Unpacking isc-dhcp-common (4.3.3-5ubuntu12.10) over (4.3.3-5ubuntu12.9) ...
Preparing to unpack .../dpkg-dev_1.18.4ubuntu1.4_all.deb ...
Unpacking dpkg-dev (1.18.4ubuntu1.4) over (1.18.4ubuntu1.3) ...
Preparing to unpack .../libdpkg-perl_1.18.4ubuntu1.4_all.deb ...
Unpacking libdpkg-perl (1.18.4ubuntu1.4) over (1.18.4ubuntu1.3) ...
Preparing to unpack .../firefox_59.0.1+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking firefox (59.0.1+build1-0ubuntu0.16.04.1) over (59.0+build5-0ubuntu0.16.04.1) ...
Preparing to unpack .../firefox-locale-en_59.0.1+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking firefox-locale-en (59.0.1+build1-0ubuntu0.16.04.1) over (59.0+build5-0ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up isc-dhcp-client (4.3.3-5ubuntu12.10) ...
Setting up isc-dhcp-common (4.3.3-5ubuntu12.10) ...
Setting up libdpkg-perl (1.18.4ubuntu1.4) ...
Setting up dpkg-dev (1.18.4ubuntu1.4) ...
Setting up firefox (59.0.1+build1-0ubuntu0.16.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (59.0.1+build1-0ubuntu0.16.04.1) ...
```

---

### Post by deadflowr on 2018-03-17
It's 
```
apt list --upgradable
```

The command
```
apt list upgradable
```
without the double dashes,
will try to show you the current list for any package called upgradable.
Which does not exist.
But you can run the command (without the double dashes (--) for actual packages and get something like
```
apt list firefox
Listing... Done
firefox/bionic,now 59.0.1+build1-0ubuntu1 amd64 [installed]
```

---

### Post by cam17 on 2018-03-21
Thank you

---

### Post by cam17 on 2018-03-21
:d

---


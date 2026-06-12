---
title: "Cannot upgrade RawTherapee from 4.0.12.0 to 4.2"
date: 2015-04-18
forum: Ubuntu/Debian BASED
---

### Post by rod6 on 2015-04-18
I currently have Rawtherapee 4.0.12.0 installed on my laptop. My OS Is Zorin OS 9.0 Core which is based on Ubuntu 14.14 LTS. Whenever I try to upgrade the RT package I get an error. Here is the output from Terminal


______________________________________________________________________


rod@p408-hplaptop:~$ sudo apt-get install rawtherapee
[sudo] password for rod: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  rawtherapee-data
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  rawtherapee
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/8,435 kB of archives.
After this operation, 10.6 MB of additional disk space will be used.
(Reading database ... 324957 files and directories currently installed.)
Preparing to unpack .../rawtherapee_4.2-4dhor~trusty_amd64.deb ...
Unpacking rawtherapee (4.2-4dhor~trusty) over (4.0.12+dfsg-2) ...
dpkg: error processing archive /var/cache/apt/archives/rawtherapee_4.2-4dhor~trusty_amd64.deb (--unpack):
 trying to overwrite '/usr/share/rawtherapee/images/curveType-flatLinear.png', which is also in package rawtherapee-data 4.0.12+dfsg-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/rawtherapee_4.2-4dhor~trusty_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rod@p408-hplaptop:~$ 


____________________________________________________________________________________




Any help is greatly appreciated. I would sure love to get this upgrade installed.


Rod

---

### Post by deadflowr on 2015-04-18
Moved to **Ubuntu/Debian BASED**

---

### Post by ajgreeny on 2015-04-18
Did you enable the ppa at [https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=trusty](https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=trusty) or did you just download the .deb for rawtherapee from a site online?

You need the ppa enabled in order to get all the dependencies.

If you already have that ppa enabled try purging your current version of rawtherapee, removing the downloaded archive from the package cache with command ```
sudo rm /var/cache/apt/archives/rawtherapee_4.2-4dhor~trusty_amd64.deb
``` and then reinstall again with the new ppa version.

That removed .deb archive may have been corrupt as it was showing an error when unpacking.  Removing it and trying again may solve the problem, but bear in mind that it could simply be a result of some different repositories that Zorin uses.

---


---
title: "Can't install dependecies"
date: 2015-07-23
forum: Ubuntu/Debian BASED
---

### Post by omar29 on 2015-07-23
I have a ubuntu 14.04.2 LTS  running on a virtual machine using Vmware and it is not the official ubuntu but rather a version called Cs50 appliance.
Anyway, suddenly the sound stopped working , so I searched for a fix and I guess I downloaded some files that aren't suitable for my version.
Now ubuntu is telling me i have problems so i used "apt-get check" and got this .
> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.7-1ubuntu4.1) but 2.4.7-1ubuntu4.4 is installed
           Depends: apache2-data (= 2.4.7-1ubuntu4.1) but 2.4.7-1ubuntu4.4 is installed
E: Unmet dependencies. Try using -f.




I tried "apt-get -f install" , to install the dependencies and overrider the wrong files, however  I got this :
> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb dmraid dpkg-repack firefox-locale-en
  gir1.2-json-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 kpartx kpartx-boot
  libdebian-installer4 libdevmapper-event1.02.1 libdmraid1.0.0.rc16
  linux-headers-3.13.0-44 linux-headers-3.13.0-44-generic
  linux-image-3.13.0-44-generic linux-image-extra-3.13.0-44-generic
  localechooser-data lvm2 python3-icu python3-pam rdate watershed
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2
Suggested packages:
  apache2-doc apache2-suexec-pristine apache2-suexec-custom apache2-utils
The following packages will be upgraded:
  apache2
1 upgraded, 0 newly installed, 0 to remove and 123 not upgraded.
Need to get 0 B/87.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 274060 files and directories currently installed.)
Preparing to unpack .../apache2_2.4.7-1ubuntu4.4_i386.deb ...
Unpacking apache2 (2.4.7-1ubuntu4.4) over (2.4.7-1ubuntu4.1) ...
dpkg: error processing archive /var/cache/apt/archives/apache2_2.4.7-1ubuntu4.4_i386.deb (--unpack):
 trying to overwrite '/etc/apache2/mods-available/dir.conf', which is also in package appliance50 2014-28
 * Restarting web server apache2                                         [ OK ] 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 /var/cache/apt/archives/apache2_2.4.7-1ubuntu4.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I would really appreciate if you helped me out with this issue and the sound issue if possible.
Thx in advance

---

### Post by PaulW2U on 2015-07-23
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by omar29 on 2015-07-25
bump

---


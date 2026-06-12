---
title: "Plesk Autoinstaller error 8.1.0"
date: 2007-02-16
forum: Server Platforms
---

### Post by Linux7 on 2007-02-16
Hi, I have an Ubuntu Plesk 8.1.0 server and did a routine run of the autoinstaller to upgrade things from the command line and I get the 1st error below.  Seems like their server doesn't have the files.

I tried to also install Plesk on a clean newly installed Ubuntu server and got the 2nd error below.  

Any idea on how to fix this or what might be causing the problem?

I also tried to install Plesk on the clean server manually but can't find the required packages Plesk says to install before installing the Plesk packages.  I can't find them on the Ubuntu CD and can't find them listed on the Ubuntu website packages area.

Anyone know where I can get them?

Thanks...



1st
**********************************************
N) Install Plesk and all required packages; P) Go back;
Q) Cancel installing; L) Show list of packages;
Select action [N]:
Start Deb-based installation with apt
Reading package lists...
Building dependency tree...
The following NEW packages will be installed:
  psa-hotfix5
The following packages will be upgraded:
  psa-horde psa-locale-base-en-us
2 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 7944kB of archives.
After unpacking 479kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  psa-horde psa-hotfix5 psa-locale-base-en-us
Authentication warning overridden.
Get:1 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) dapper/all psa-horde 3.1.3-ubuntu6.06.build81070201.15 [6041kB]
Err [http://autoinstall.plesk.com](http://autoinstall.plesk.com) dapper/all psa-horde 3.1.3-ubuntu6.06.build81070201.15
  Error reading from server. Remote end closed connection
Get:2 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) dapper/all psa-hotfix5 8.1.0-ubuntu6.06.build81070201.15 [152kB]
Get:3 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) dapper/all psa-locale-base-en-us 8.1.0-ubuntu6.06.build81070201.15 [1752kB]
Failed to fetch [http://autoinstall.plesk.com/ubuntu/PSA_8.1.0/../../PSA_8.1.0/dist-deb-Ubuntu-6.06-i386//base/psa-horde_3.1.3-ubuntu6.06.build81070201.15_i386.deb](http://autoinstall.plesk.com/ubuntu/PSA_8.1.0/../../PSA_8.1.0/dist-deb-Ubuntu-6.06-i386//base/psa-horde_3.1.3-ubuntu6.06.build81070201.15_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
Fetched 1904kB in 20s (92.9kB/s)
ERROR: Install command execution failed
Errors just before:
- Can't execute package installation command

ERROR: Installation failed




2nd
**********************************************
N) Next page; P) Go back;  Q) Cancel installing;
A) Select all; D) Deselect all;
To toggle component enter its number;
Type a number or a character of desired action [N]:
resolve packages with apt-get
E: Version '3.1.3-ubuntu6.06.build81070201.15' for 'psa-horde' was not found
apt-get say following:
Reading package lists...
Building dependency tree...

ERROR: Error while resolve packages by apt




3rd
**********************************************
Install the packages of indicated versions or higher from the Ubuntu-6.06 i386 disc:

'''update-deb-Ubuntu-6.06-i386/'''

j2re1.4_1.4.2.01-1_i386.deb
php4-ioncube-loader_3.0-ubn60.build06101212_i386.deb
php5-ioncube-loader_3.0-ubn60.build06101212_i386.deb
j2sdk1.4_1.4.2.01-1_i386.deb
psa-php4-configurator_1.1.0-ubuntu6.06.build81061129.23_all.deb
psa-php5-configurator_1.1.0-ubuntu6.06.build81061129.23_all.deb
ERROR: Installation failed

---


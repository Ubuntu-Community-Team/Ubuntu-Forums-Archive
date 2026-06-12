---
title: "About notice of latest VirtualBox version"
date: 2017-05-07
forum: Virtualisation
---

### Post by satimis on 2017-05-07
Hi all,

Host - Ubuntu16.04
VMs - Ubuntu/Debian/Mint/Windows etc
Virtualbox - Version 5.0.26 r108824

This box has been running at least 4 years.  I can't recall whether VirtualBox was installed on repo or download on its website.

Each day when VirtuaLbox is first started following warning popup
(see attached image - screenshot_virtualbox.png)

The running version of VirtualBox 
(see attached image - screenshot_virtualbox_running_version.png)

Please advise what shall I do, download the latest version and install it running dkpg?```

sudo dpkg -i DEB_PACKAGE

```

Would the installation affect the VMs installed? (I would shutdown all VMs)

Please advise.  Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-05-07
> **satimis said:**
> Please advise what shall I do
That's up to you.  You could install the latest version.  You could install the [latest 5.0 version]("https://www.virtualbox.org/wiki/Download_Old_Builds_5_0").  You could also just ignore the notice and go on using the version you've got, if it works for you.

The [changelogs]("https://www.virtualbox.org/wiki/Changelog") might help you decide.

**Do be sure to backup your system _before_ changing VirtualBox version.**

> Would the installation affect the VMs installed? (I would shutdown all VMs)
Yes and no.  With a VirtualBox upgrade comes a Guest Additions upgrade.  It would be smart to reinstall the newer Guest Additions on your VMs that have Guest Additions installed, especially if you're changing major VirtualBox version like 5.0 -> 5.1.

---

### Post by satimis on 2017-05-07
> **halogen2 said:**
> 
- snip -

You could also just ignore the notice and go on using the version you've got, if it works for you.

- snip -

Hi,

Thanks for your advice.

This box is running without problem.  It is a strong box with AMD 8-core CPU, 32G RAM, 1TB SSD.

I'll take your advice just ignoring the notice until building a new box.  I'm waiting for AMD 10-core CPU

"Virtualbox - Version 5.0.26 r108824" is it a repo version?

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-05-07
> **satimis said:**
> "Virtualbox - Version 5.0.26 r108824" is it a repo version?
I don't use the repo version, so can't tell from just that.  One way to tell is to run this command -
```
dpkg-query -W | grep -i virtualbox
```

On my system, it outputs this -
```
$ dpkg-query -W | grep -i virtualbox
virtualbox-5.1  5.1.18-114002~Ubuntu~xenial

```
Notice that it says "virtualbox-5.1" for the package name.  That's a version downloaded from the official site.  If from the repos, it will say just "virtualbox" and you may get more than one package listed.  If your VirtualBox is a download from the official site, when you run the command it'll show a package named "virtualbox-5.0".

---

### Post by satimis on 2017-05-07
> **halogen2 said:**
> I don't use the repo version, so can't tell from just that.  One way to tell is to run this command -
```
dpkg-query -W | grep -i virtualbox
```

On my system, it outputs this -
```
$ dpkg-query -W | grep -i virtualbox
virtualbox-5.1  5.1.18-114002~Ubuntu~xenial

```
Notice that it says "virtualbox-5.1" for the package name.  That's a version downloaded from the official site.  If from the repos, it will say just "virtualbox" and you may get more than one package listed.  If your VirtualBox is a download from the official site, when you run the command it'll show a package named "virtualbox-5.0".
Hi,

&#10219; dpkg-query -W | grep -i virtualbox```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox-4.3  4.3.32-103443~Ubuntu~raring
virtualbox-5.0  5.0.26-108824~Ubuntu~trusty
```

&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

```

Why there are 2 version of VirtualBox?

satimis@ub1604ssd1tb:~&#10219; apt-cache policy virtualbox```

virtualbox:
  Installed: (none)
  Candidate: 5.0.14-dfsg-2
  Version table:
     5.0.14-dfsg-2 500
        500 http://ubuntu.01link.hk xenial/multiverse amd64 Packages
```
Not installed?

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-05-08
> **satimis said:**
> Why there are 2 version of VirtualBox?
Umm.  Not only do you have two VirtualBox packages both installed from the official site, they're both intended for older versions of Ubuntu than your 16.04.  Not sure how that happened.  I'm surprised it works at all.

I would recommend backing up your system, then cleaning that up.  First purge both packages -
```
sudo apt-get purge 'virtualbox-*'
```

Then download and install VirtualBox 5.0.26 for Xenial from the link I gave for latest 5.0.  You'll also need to reinstall the Extension Pack version 5.0.26 if you had it installed before.

> Not installed?
Indeed not.  That's the repo version, which you're not using.

---

### Post by satimis on 2017-05-08
> **halogen2 said:**
> Umm.  Not only do you have two VirtualBox packages both installed from the official site, they're both intended for older versions of Ubuntu than your 16.04.  Not sure how that happened.  I'm surprised it works at all.

I would recommend backing up your system, then cleaning that up.  First purge both packages -
```
sudo apt-get purge 'virtualbox-*'
```

Then download and install VirtualBox 5.0.26 for Xenial from the link I gave for latest 5.0.  You'll also need to reinstall the Extension Pack version 5.0.26 if you had it installed before.


Indeed not.  That's the repo version, which you're not using.
Hi,

Thanks for your advice.

I also wonder how this could happen?  The only explanation is this box was upgraded from Ubuntu 14.04 to Ubuntu 16.04.

I prefer to do a clean installation as I'm prepared to purchase a new 2TB SSD.  Please see my another posting on;

How to move VMs in group?
[https://ubuntuforums.org/showthread.php?t=2360737&p=13642709#post13642709](https://ubuntuforums.org/showthread.php?t=2360737&p=13642709#post13642709)

I have done migrating VM before but one by one.  It will take me some time to complete my job as I have 41 VMs installed.  I'm interested to know whether there will a method of group migration copying all VMs to the new C-drive in one operation.

I won't delete the running C-drive first until I have tested the new C-drive after migration, confirming it without problem.

Regards
satimis

---

### Post by satimis on 2017-05-09
Hi halogen2,

I have a spare PC, say PC-2, with following configuration:
CPU - AMD 8-core
RAM - 8G
SSD 120G - for OS
WD Black HD 1TB - for storage (all VM images stored here)

This box was built about 6/7 years ago.  It is not a slow machine but with only 8G RAM onboard.

Daily working PC. say PC-1;
CPU - AMD 8-core
RAM - 32G
SSD 1TB

Just testing Export/Import VM suggested by "TheFu" on #2 of follwoing link;
[https://ubuntuforums.org/showthread.php?t=2360737&p=13642709#post13642709](https://ubuntuforums.org/showthread.php?t=2360737&p=13642709#post13642709)

It worked seamlessly, with Android-x86.ova imported to VirtualBox of this PC-2

PC-2
Host - Ubuntu 16.04 also upgraded from 14.04

&#10219; dpkg-query -W | grep -i virtualbox```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox      4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1
virtualbox-4.3  4.3.36-105129~Ubuntu~raring
virtualbox-5.0  5.0.26-108824~Ubuntu~trusty
virtualbox-qt   4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1

```

&#10219; apt-cache policy virtualbox```

virtualbox:
  Installed: (none)
  Candidate: 5.0.36-dfsg-0ubuntu1.16.04.2
  Version table:
     5.0.36-dfsg-0ubuntu1.16.04.2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
     5.0.18-dfsg-2build1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
     4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1 0
        100 /var/lib/dpkg/status

```

There are only 8 VMs installed here.  I'm prepared testing your suggestion on #6 above running```

sudo apt-get purge 'virtualbox-*'

```

Do I need to backup the complete C-drive here, 120G SSD for running OS only?  Or just "Export" the VMs as .ova images to the storage drive and "Import" them to VirtualBox afterwards, in case of problem?

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-05-09
I would back up the whole system.  The concern there is not only your VMs.

That computer seems to additionally have the repo version of VirtualBox installed.  The purge command I suggested may not get it, so try this instead -
```
sudo apt-get purge virtualbox 'virtualbox-*'
```

---

### Post by SeijiSensei on 2017-05-09
If you are re-installing VirtualBox from scratch, I strongly recommend that you follow the method described here:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

If you add Oracle's PPA, VirtualBox updates will happen alongside other system updates.  You'll be prompted to update the Extension Pack, but that's easily done from the GUI, though perhaps not for lots of VMs.  There must be a scriptable way as well.

I've moved VMs from machine to machine and upgraded from VB 5.0 to 5.1 over them.  (I've tried running them over NFS, but my network speeds aren't high enough for decent performance.  My central server is old and still has a 100Mbit card.)  All the VM images should be stored in a "VirtualBox VMs" directory under the home directory of the user running VirtualBox.  After copying that directory to a new host, I've gone through the process of adding each machine to the list from the GUI menu using Machine >Add and pointing to the appropriate .vbox file when prompted.  Again if you have a lot of machines to create, using the command-line tools in a script would probably be far easier and quicker.

---

### Post by satimis on 2017-05-10
> **SeijiSensei said:**
> If you are re-installing VirtualBox from scratch, I strongly recommend that you follow the method described here:  [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

- snip -

Hi,

Thanks for your advice and link.

PC-1 (daily working machine)

&#10219; ls /home/satimis/VirtualBox\ VMs/```

Android-x86             ub1404dkpc1a_00    ub1604dkpc1_002
android-x86-6.0-r2      ub1404dkPC1A00     ub1604dkpc1_01
android-x86-6.0-r2-02   ub1404dkpc1a_01    ub1604dkpc1_02
HAProxy                 ub1404dkPC1A01     ub1604dkpc1_03
kub1604.1pc1a00         ub1404dkpc1a_02    ub1604dkpc1_04
lamp00pc1a              ub1404dkPC1A02     ub1604dkpc1_05
lesousvidepc1a          ub1404dkpc1a_03    ub1604dkpc1_06
load_balancing          ub1404dkpc1a_04    websites-cloned
localsites              ub1404dkssd1t_00   Win10home
music_pc1a              ub1404server1t_00  Win10home_01
New group               ub1404server1t_01  Win10pro_00
Remix OS                ub1404server1t_02  Win10pro_01
ub1404dk_lamp_pc1a_00   ub1604dkpc1_00     wp00pc1a
ub1404dk_lamp_pc1a_000  ub1604dkpc1_001    wp412_ub1404server_00

```

&#10219; ls /home/satimis/VirtualBox\ VMs/New\ group/```

ub1604dkpc1_03

```

I'm not aware when this "New group" was created.  I will rename ub1604dkpc1_03 as ub1604dkpc1_07 and move it back to the original group.  Then I'll delete the "New group" folder.

Can I do all steps on Terminal?


PC-2 (Spare PC)
"VirtualBox VMs" folder is on another drive

VirtualBox Manager
File -> Preference
-> General
Default Machine Folder: /media/satimis/c522222xxxxxxxx/VM_core_VDI

If I delete /media/satimis/c522222xxxxxxxx/VM_core_VDI (this link), the VMs are still on the Virtual Machine Manager.  But they are unable to start

Whether I just delete the link and run```

sudo apt-get remove virtualbox* --purge

```
to remove all following packages;```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox      4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1
virtualbox-4.3  4.3.36-105129~Ubuntu~raring
virtualbox-5.0  5.0.26-108824~Ubuntu~trusty
virtualbox-qt   4.3.36-dfsg-1+deb8u1ubuntu1.14.04.1

```

After reinstall the latest VirtualBox download on Orcle site, then I'll put the link back?  Or still I have to import VMs one by one?

After successful I'll come back to PC-1.

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-05-10
> **satimis said:**
> PC-2 (Spare PC)
"VirtualBox VMs" folder is on another drive

VirtualBox Manager
File -> Preference
-> General
Default Machine Folder: /media/satimis/c522222xxxxxxxx/VM_core_VDI

If I delete /media/satimis/c522222xxxxxxxx/VM_core_VDI (this link), the VMs are still on the Virtual Machine Manager.  But they are unable to start

Whether I just delete the link a
What link?  Since you've shut down all your VMs - you shouldn't have to touch your VMs, nor your VMs folder, before the uninstall/reinstall.

---

### Post by satimis on 2017-05-11
> **halogen2 said:**
> What link?  Since you've shut down all your VMs - you shouldn't have to touch your VMs, nor your VMs folder, before the uninstall/reinstall.
Ah I see all VMs are NOT running.

Besides I'll stop the Virtual Machine Manager running as well.

Thanks

Regards
satimis

---

### Post by SeijiSensei on 2017-05-11
> **satimis said:**
> 
Can I do all steps on Terminal?
To transfer the "VirtualBox VMs" directory you can use rsync.  As I said before, I'm not familiar enough with the [command-line tools for VirtualBox]("https://www.virtualbox.org/manual/ch08.html#idm3463") to know if you can use them to register all your virtual machines, but it looks like you can.

> After reinstall the latest VirtualBox download on Orcle site, then I'll put the link back?  Or still I have to import VMs one by one?
Just to make sure. You're not "downloading" the VirtualBox .deb file directly.  The method described lets you define a PPA from which to obtain VirtualBox using normal Ubuntu tools like apt or the Software Center.  Then when you install the virtualbox-5.1 package it will come from Oracle's servers, not Canonical's.  The program will be updated when necessary just like all the other packages on your computer.

---

### Post by satimis on 2017-05-11
> **SeijiSensei said:**
> To transfer the "VirtualBox VMs" directory you can use rsync.  As I said before, I'm not familiar enough with the [command-line tools for VirtualBox]("https://www.virtualbox.org/manual/ch08.html#idm3463") to know if you can use them to register all your virtual machines, but it looks like you can.
Noted and thanks.

I use rsync a lot transferring data amongst PCs on internal network

> 
Just to make sure. You're not "downloading" the VirtualBox .deb file directly.  The method described lets you define a PPA from which to obtain VirtualBox using normal Ubuntu tools like apt or the Software Center.  Then when you install the virtualbox-5.1 package it will come from Oracle's servers, not Canonical's.  The program will be updated when necessary just like all the other packages on your computer.
In the past I installed VirtualBox on the package download on Oracle website.  But later I installed it on Ubuntu repo.

This time I'll run ```

apt-get install virtualbox

```
to install it on Ubuntu package

satimis

---

### Post by satimis on 2017-05-15
> **halogen2 said:**
> I would back up the whole system.  The concern there is not only your VMs.

That computer seems to additionally have the repo version of VirtualBox installed.  The purge command I suggested may not get it, so try this instead -
```
sudo apt-get purge virtualbox 'virtualbox-*'
```
Hi,

PC-2
====
Performed following steps:-

&#10219; sudo apt-get purge virtualbox 'virtualbox-*'
It went through without complaint

&#10219; sudo apt-get install virtualbox
Also it went through without complaint

&#10219;  dpkg-query -W | grep -i virtualbox```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox      5.0.40-dfsg-0ubuntu1.16.04.1
virtualbox-dkms 5.0.40-dfsg-0ubuntu1.16.04.1
virtualbox-qt   5.0.40-dfsg-0ubuntu1.16.04.1

```

On terminal start VirtualBox Manger
All VMs are there but on starting them following warning popup```

Failed to open a session for the virtual machine Classic.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings.

Note! This error could also mean that an incompatible version of the 'Oracle VM VirtualBox Extension Pack' is installed (VERR_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```

&#10219; apt-cache search virtualbox | grep virtualbox-* | grep ext```

virtualbox-ext-pack - extra capabilities for VirtualBox, downloader.

```

Shall I install this package?

Also I download the extension pack here;

VirtualBox 5.0.40 (released April 28th 2017)
[https://www.virtualbox.org/wiki/Download_Old_Builds_5_0](https://www.virtualbox.org/wiki/Download_Old_Builds_5_0)

Oracle_VM_VirtualBox_Extension_Pack-5.0.40-115130.vbox-extpack

Is it the right package?  If YES how to install it?

Thanks

Regards
satimis

---

### Post by satimis on 2017-05-15
Hi all,

I followed below document installing the external pack:-
How to install VirtualBox Extension Pack
itzgeek.com/how-tos/mini-howtos/how-to-install-virtualbox-extension.html

The extension pack was download on Orcle website to Downloads/ folder

&#10219; cd Downloads/
&#10219; ls
Oracle_VM_VirtualBox_Extension_Pack-5.0.40-115130.vbox-extpack

&#10219; sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-5.0.40-115130.vbox-extpack```

.....
Do you agree to these license terms and conditions (y/n)? y
License accepted. For batch installaltion add
--accept-license=715c7246dc0f779ceab39446812362b2f9bf64a55ed5d3a905f053cfab36da9e
to the VBoxManage command line.

0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully installed "Oracle VM VirtualBox Extension Pack".

```

The previously installed VMs are now running again.  VM exported from PC-1 can be imported here.

Since the VMs in PC-2 are installed on WD Black Label HD they are running quite slow compaired to VMs on PC-2.  The latter are running and installed on SSD.

I think it is the time for me to purchase a 1TB SSD and install it on PC-2.  Unfortunate the price of SSD remains almost stable.

I'll export all VMs of PC-1 to PC-2 first before starting to wipe out the VirtualBox there and reinstall it on Ubuntu repo.

Thanks

Regards
satimis

---

### Post by satimis on 2017-05-19
Hi all,

PC-1
====
After exporting all VMs performed following steps;

Making sure Oracle VM VirtualBox Manager NOT running

&#10219; dpkg-query -W | grep -i virtualbox```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox-4.3  4.3.32-103443~Ubuntu~raring
virtualbox-5.0  5.0.26-108824~Ubuntu~trusty

```

&#10219; sudo apt-get purge virtualbox 'virtualbox-*'```

......
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 libvpx1
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-4.3* virtualbox-5.0*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 155 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 258945 files and directories currently installed.)
Removing virtualbox-4.3 (4.3.32-103443~Ubuntu~raring) ...
Purging configuration files for virtualbox-4.3 (4.3.32-103443~Ubuntu~raring) ...
Removing virtualbox-5.0 (5.0.26-108824~Ubuntu~trusty) ...
Purging configuration files for virtualbox-5.0 (5.0.26-108824~Ubuntu~trusty) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...

```

&#10219; apt-cache policy virtualbox```

virtualbox:
  Installed: (none)
  Candidate: 5.0.14-dfsg-2
  Version table:
     5.0.14-dfsg-2 500
        500 http://ubuntu.01link.hk xenial/multiverse amd64 Packages

```

I don't know why Ubuntu repo providing the old version 5.0.14 ?
==============================================

&#10219; sudo apt-get update ; sudo apt-get upgrade```

Hit:1 [http://ubuntu.01link.hk](http://ubuntu.01link.hk) xenial InRelease
Hit:2 [http://ubuntu.01link.hk](http://ubuntu.01link.hk) xenial-updates InRelease
Hit:3 [http://ubuntu.01link.hk](http://ubuntu.01link.hk) xenial-backports InRelease                      
Hit:4 [http://ubuntu.01link.hk](http://ubuntu.01link.hk) xenial-security InRelease                       
Reading package lists... Done                                                 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
....
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

&#10219; sudo apt-get install virtualbox```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libgnutls-deb0-28 libgsoap7 libvncserver1 virtualbox-dkms virtualbox-qt
Suggested packages:
  gnutls-bin vde2 virtualbox-guest-additions-iso
The following NEW packages will be installed:
  libgnutls-deb0-28 libgsoap7 libvncserver1 virtualbox virtualbox-dkms
  virtualbox-qt
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.6 MB of archives.
After this operation, 95.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
......
vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-59-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-59-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-59-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-59-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up virtualbox (5.0.14-dfsg-2) ...
vboxweb.service is a disabled or a static unit, not starting it.
Setting up virtualbox-qt (5.0.14-dfsg-2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for systemd (229-4ubuntu16) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for menu (2.1.47ubuntu1) ...

```

&#10219; virtualbox
starting Oracle VM VirtualBox Manager
all VMs are there

Starting VM following warning popup;```

Failed to open a session for the virtual machine ub1604dkpc1_03.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings.

Note! This error could also mean that an incompatible version of the 'Oracle VM VirtualBox Extension Pack' is installed (VERR_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```

&#10219; dpkg-query -W | grep -i virtualbox```

unity-scope-virtualbox  0.1+13.10.20130723-0ubuntu1
virtualbox      5.0.14-dfsg-2
virtualbox-dkms 5.0.14-dfsg-2
virtualbox-qt   5.0.14-dfsg-2

```

Download the extension pack;
[https://www.virtualbox.org/wiki/Download_Old_Builds_5_0_pre18](https://www.virtualbox.org/wiki/Download_Old_Builds_5_0_pre18)

to Downloads/  (folder)

&#10219; ls Downloads/ | grep Oracle```

Oracle_VM_VirtualBox_Extension_Pack-5.0.14-105127a.vbox-extpack

```

&#10219; cd Downloads/
&#10219; sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-5.0.14-105127a.vbox-extpack ```

.....
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully installed "Oracle VM VirtualBox Extension Pack".

```

Install VBoxGuestAdditions_5.0.14.iso online
Warning```

The image file '/home/satimis/Downloads/VBoxGuestAdditions_5.0.14.iso' is inaccessible and is being ignored. Please select a different image file for the virtual DVD drive..
Error ID: 
DvdOrFloppyImageInaccessible
Severity: 
Warning

```

Download VBoxGuestAdditions_5.0.14.iso on;
[http://download.virtualbox.org/virtualbox/5.0.14/](http://download.virtualbox.org/virtualbox/5.0.14/)
to /Downloads folder

&#10219; ls Downloads/ | grep VBoxGuestAdditions```

VBoxGuestAdditions_5.0.14.iso

```

Installed VBoxGuestAdditions_5.0.14.iso manually on VM

Restarted VM

All done

I think it needing quite some time to install VBoxGuestAdditions_5.0.14 on all VMs

Regards
satimis

---

### Post by JKyleOKC on 2017-05-22
The reason for still having the older version in the repos is simple: It's *buntu policy to NOT upgrade repo packages, once a release is frozen, except for security reasons. That's why many of us install Oracle's PPA into the sources.list file and get updates from the horse's mouth instead of staying with the frozen version which may be more than two years old by now.

I've been using vbox for quite a few years. Initially, I moved VMs from one box to another by simply moving their virtual-disk files, creating a new VM on the target box, and attaching the copied disk to it. For years, this worked, but Oracle seems to have tightened up some of the code and I discovered a couple of years ago that the copied disk file didn't always get registered at its new location.

In the past several months, I've switched to using the import/export facility to create OVA or OVF files on the original machine, copying those much smaller files to the target machine, then importing from them. This seems to be working perfectly -- and the OVA/OVF files serve me as backups with the sole disadvantage that data entered after they are created isn't in them. Since vbox itself is multi-platform, these files allow me to take my critical VMs to any available system if need be to continue critical tasks!

---

### Post by satimis on 2017-05-23
> **JKyleOKC said:**
> The reason for still having the older version in the repos is simple: It's *buntu policy to NOT upgrade repo packages, once a release is frozen, except for security reasons. That's why many of us install Oracle's PPA into the sources.list file and get updates from the horse's mouth instead of staying with the frozen version which may be more than two years old by now.

I've been using vbox for quite a few years. Initially, I moved VMs from one box to another by simply moving their virtual-disk files, creating a new VM on the target box, and attaching the copied disk to it. For years, this worked, but Oracle seems to have tightened up some of the code and I discovered a couple of years ago that the copied disk file didn't always get registered at its new location.

In the past several months, I've switched to using the import/export facility to create OVA or OVF files on the original machine, copying those much smaller files to the target machine, then importing from them. This seems to be working perfectly -- and the OVA/OVF files serve me as backups with the sole disadvantage that data entered after they are created isn't in them. Since vbox itself is multi-platform, these files allow me to take my critical VMs to any available system if need be to continue critical tasks!
Hi,

Thanks for your detail advice.

I have been running VirtualBox for many years.  Before I ran KVM and VirtualBox simultaneously and later I dropped KVM.

In previous time I installed VirtualBox from the packages download on Oracle's website.  This time I reinstalled VirtualBox on repos and found it a old version.  I'll keep on running it until I build a new AMD Ryzen 16 core box.  This working PC has been serving me for several year (>7 years).  Although it is a powerful box it is time for it to retire.

Regards
satimis

---


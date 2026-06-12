---
title: "Unable to start VM after upgrade"
date: 2017-10-19
forum: Virtualisation
---

### Post by satimis on 2017-10-19
Hi all,

Host - Ubuntu 16.04 desktop
VM - Ubuntu 16.04 desktop
Oracle VirtualBox

Recently I have upgraded Ubuntu 16.04 (Host) by changing to another repo (Download from: Server for Hong Kong).  Please see following posting:-

[https://ubuntuforums.org/showthread.php?t=2374382&page=3](https://ubuntuforums.org/showthread.php?t=2374382&page=3)
# 27

After upgrade I'm unable to start VM

Warning:```

Failed to open a session for the virtual machine ub1604dkpc1_00.

The device helper structure version has changed.

If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

```

&#10219; vboxmanage --version```

5.0.40_Ubuntur115130

```

Virtual-Manager
-> Preferences -> Extensions
Extension Packages```

(check) Oracle VM VirtualBox Extension Pack  5.0.14r105127
(check) VNC  5.0.40r115130

```

Please advise how to fix the problem.  Thanks

Regards
satimis

---

### Post by satimis on 2017-10-21
Hi all,

Finally  I have to reinstall VirtualBox

Performed following steps

1)
Download VirtualBox for Linux Hosts
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)
virtualbox-5.2_5.2.0-118431~Ubuntu~xenial_amd64.deb

2)
Uninstall VirtualBox

&#10219; sudo apt-get remove virtualbox```

[sudo] password for satimis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsoap8 libvncserver1 virtualbox-dkms
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox virtualbox-qt
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 90.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 259638 files and directories currently installed.)
Removing virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Removing virtualbox (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...

```

3)
Uninstall VirtualBox DKMS

&#10219; sudo apt-get remove virtualbox-dkms```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsoap8 libvncserver1
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 5,049 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 259340 files and directories currently installed.)
Removing virtualbox-dkms (5.0.40-dfsg-0ubuntu1.16.04.1) ...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.0.40
Kernel:  4.4.0-59-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.0.40
Kernel:  4.4.0-97-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-97-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-97-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-97-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-97-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
------------------------------
Deleting module version: 5.0.40
completely from the DKMS tree.
------------------------------
Done.

```


4)
Install the downloaded package virtualbox-5.2_5.2.0-118431~Ubuntu~xenial_amd64.deb

&#10219; sudo dpkg -i Downloads/virtualbox-5.2_5.2.0-118431~Ubuntu~xenial_amd64.deb```
 
Selecting previously unselected package virtualbox-5.2.
(Reading database ... 259057 files and directories currently installed.)
Preparing to unpack .../virtualbox-5.2_5.2.0-118431~Ubuntu~xenial_amd64.deb ...
Unpacking virtualbox-5.2 (5.2.0-118431~Ubuntu~xenial) ...
Setting up virtualbox-5.2 (5.2.0-118431~Ubuntu~xenial) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu19) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...

```

Start VirtualBox

VitualBox - Question```

You have an old version (5.0.14) of the Oracle VM VirtualBox Extension Pack installed.
Do you wish to download latest one from the Internet?
-> [Download]

```

VitualBox - Question```

The Oracle VM VirtualBox Extension Pack has been successfully downloaded from http://download.virtualbox.org/virtualbox/5.2.0/Oracle_VM_VirtualBox_Extension_Pack-5.2.0.vbox-extpack and saved locally as /home/satimis/.config/VirtualBox/Oracle_VM_VirtualBox_Extension_Pack-5.2.0.vbox-extpack.
Do you wish to install this extension pack?
-> [Install]

```

VitualBox - Question```

An older version of the extension pack is already installed, would you like to upgrade? 
Extension packs complement the functionality of VirtualBox and can contain system level software that could be potentially harmful to your system. Please review the description below and only proceed if you have obtained the extension pack from a trusted source.

Name:  
Oracle VM VirtualBox Extension Pack
New Version:  
5.2.0r118431
Current Version:  
5.0.14r105127
Description:  
USB 2.0 and USB 3.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM, Disk Encryption, NVMe.
-> [Upgrade]

```

VitualBox - Question```

The extension pack 
Oracle VM VirtualBox Extension Pack
was installed successfully.
-> [OK]

```

VitualBox - Question```

Do you want to delete the downloaded file /home/satimis/.config/VirtualBox/Oracle_VM_VirtualBox_Extension_Pack-5.2.0.vbox-extpack?
-> [Delete]

```


VitualBox - Question```

Do you want to delete following list of files Oracle_VM_VirtualBox_Extension_Pack-4.3.28.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-4.3.30.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-4.3.32.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.10.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.12.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.14.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.16.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.18.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.20.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.24.vbox-extpack,Oracle_VM_VirtualBox_Extension_Pack-5.0.26.vbox-extpack?
-> [Delete]

```

&#10219; vboxmanage --version```

5.2.0r118431

```


&#10219; systemctl reboot


Start VirtualBox
Now VMs can be started
Remark:  I only checked several of them.


I think the VirtualBox package on the repo is NOT up-to-date?

Problem is now solved.

Regards
satimis

---

### Post by Rick St. George on 2017-10-22
This seems to be common after an upgrade. Apparently the Repos are not upgraded as along with. Doubt this can be programmed to happen during an upgrade. Therefore, we have to disable all Repos, after upgrade - Find new Repos (and/or wait until they are available) and the Add the new Repos for your newer OS version. Understand that the programs you have installed (non Canonical supported) may be broken until you can add the new repos and update those programs. 

So, bottom line - WAIT until Repos are available for you newer version - before upgrading.

Peace!
Rick
):P

---

### Post by satimis on 2017-10-22
> **Rick St. George said:**
> This seems to be common after an upgrade. Apparently the Repos are not upgraded as along with. Doubt this can be programmed to happen during an upgrade. Therefore, we have to disable all Repos, after upgrade - Find new Repos (and/or wait until they are available) and the Add the new Repos for your newer OS version. Understand that the programs you have installed (non Canonical supported) may be broken until you can add the new repos and update those programs. 

So, bottom line - WAIT until Repos are available for you newer version - before upgrading.

Peace!
Rick
):P
Hi Rick,

Thanks for your advice.  I would stop running "update and upgrade" until the new repos are available.  We have no idea when but only waiting with patience.

Regards
satimis

---


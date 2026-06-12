---
title: "I've done something wrong, what should I do?"
date: 2009-12-08
forum: Server Platforms
---

### Post by MKVCrazy on 2009-12-08
I am running Ubuntu Server 9.04 64-Bit. And I wanted to install GNOME Desktop Enviroment but I mistakenly entered the GNOME installation which comes with the recommended default apps like Empathy or OpenOffice etc, since this is on a server I don't need them and I want my server as light weight as possible. So I am planning to install the GNOME without those recommended stuff.

But I ran the one with default apps and I did reboot while it wasn't done installing using the following command if it matters:
```
sudo reboot
```So it rebooted and I can still access the server fine but I am not sure what happened to the installation of GNOME with recommended apps that was running. So if I want to install the one without recommended apps, must I first make my Ubuntu Server clean or when I do the installation the new one will just overwrite on the half installed one?

```
sudo aptitude install -- no-install-recommends ubuntu-desktop
```Oh by the way, when I enter the above command I get the following errors and I don't think it install the GNOME.
```
admin@XXXXX:~# sudo aptitude install -- no-install-recommends ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Couldn't find any package whose name or description matched "no-install-recommends"
Couldn't find any package whose name or description matched "no-install-recommends"
The following partially installed packages will be configured:
  acpi-support acpid ubuntu-desktop 
0 packages upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```Please advice what to do next.

---

### Post by Iowan on 2009-12-08
[https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by MKVCrazy on 2009-12-08
```
sudo aptitude install ubuntu-desktop
```Thank you for the link but when I type in the above in the command I get the follow errors.

The errors:
```
root@XXXXX:~# sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  acpi-support acpid ubuntu-desktop 
0 packages upgraded, 3 newly installed, 0 to remove and 56 not upgraded.
Need to get 0B/103kB of archives. After unpacking 995kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package acpid.
(Reading database ... 104628 files and directories currently installed.)
Unpacking acpid (from .../acpid_1.0.6-9ubuntu4.9.04.3_amd64.deb) ...
Selecting previously deselected package acpi-support.
Unpacking acpi-support (from .../acpi-support_0.121_amd64.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.140_amd64.deb) ...
Processing triggers for man-db ...
Setting up acpid (1.0.6-9ubuntu4.9.04.3) ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 acpid
 acpi-support
 ubuntu-desktop
```

---

### Post by MKVCrazy on 2009-12-09
I've tried many things. But whenever I try to install "ubuntu-desktop" **acpid** and **acpid-support** are always included and when I see those two I know I am gonna get the above ERROR that I posted in my previous reply.

Please help how to solve this.

```
root@XXXXX:~# sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acpi-support acpid
The following NEW packages will be installed
  acpi-support acpid ubuntu-desktop
0 upgraded, 3 newly installed, 0 to remove and 56 not upgraded.
Need to get 103kB of archives.
After this operation, 995kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by MKVCrazy on 2009-12-11
Problem SOLVED

---


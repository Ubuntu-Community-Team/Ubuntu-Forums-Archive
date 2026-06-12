---
title: "Ubuntu 10.04 errors after Weblogic install"
date: 2010-09-10
forum: Virtualisation
---

### Post by chibern on 2010-09-10
I am having an issue with my VirtualBox setup. Please excuse my ignorance on any issues as I am a Linux and VB newbie.  I posted this in the VirtualBox forum and they referred me here.

I have created a VM with 2GB mem, 16GB virtual drive, 64MB video memory running on a 6GB Win7 64-bit host. My ultimate goal is to have a SOA development environment.

Installed Ubuntu 10.04, 32-bit. No issues.
Installed VB Guest Additions (VBoxLinuxAdditions-x86). No issues.
Installed Oracle XE database. No issues.
Applied the RCU. No issues.
Installed Java JDK 1.6.0_20. No issues

Every boots up fine and is accessible and Guest Additions has been working fine up until this point.

After I install Weblogic 10.3.3 (i've tried both the .jar and .bin) the VM will not boot to the GUI desktop anymore. The VM resizes the window about 10 times and then gives the following error.

(EE) [drm] drmOpen Failed.
(EE) VBoxVideo(0): DRIScreenInit Failed, disabling DRI.
(EE) VirtualBox USB Tablet: failed to initialized for relative axes.

the log file has something like this:
drmOpenDevice:node name is /dev/dri/card0
[drm] failed to load kernel module "vboxvideo"
(EE) [drm] drmOpen Failed.
(EE) VBoxVideo(0): DRIScreenInit Failed, disabling DRI.

Then the only way I can get to the console is if I use root user. If I try to log on as my normal user, I get a permission error on /bin/bash.

Another thing is that immediately after I install Weblogic, I cannot open a command window from the GUI or run anything in an already open command window (even with sudo). Once I reboot I am no longer able to access the desktop nor log on as a normal user.

I am assuming the Weblogic install messed something up but I'm not sure where to look.

This issue is repeatable.  I have an image saved immediately after the Java install where everything still works.  Each time I install Weblogic onto this image the same thing happens.

I know this is a pretty specific issue so thanks for any help!

---

### Post by KSky on 2010-10-22
I faced the same issue on actual Fedora 10 and Ubuntu 10.10 installations. Still don't know the actual reason nor a fix.

In case anyone has come across this issue please post a solution.

---

### Post by tejdig on 2010-11-05
I guess you installed WebLogic using root user? this is not recommended. I have seen this before where the installer changes the permissions on /bin to 700. you might want verify that and change to 755. That should fix it

---


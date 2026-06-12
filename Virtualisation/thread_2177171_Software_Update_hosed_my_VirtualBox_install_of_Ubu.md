---
title: "Software Update hosed my VirtualBox install of Ubuntu 13"
date: 2013-09-27
forum: Virtualisation
---

### Post by icculus2 on 2013-09-27
I've been running Ubuntu 13 in VirtualBox (Win7 host) for several weeks and it's worked great.  This morning, Ubuntu Software Update came up and wanted to install a general update.  I didn't look at the details but I remember it was about 60MB worth of updates.  After the update, it seems that my Guest Additions no longer work; my screens will not go fullscreen and the mouse is very laggy when it shows up at all (the last few reboots it does not display the cursor at all meaning the system is unusable).  I've installed the Guest Additions by way of ISO as well as sudo apt-get install virtualbox-guest-additions-iso.  Both succeed (slightly different versions), but neither fix my problems.  I'm looking at having to completely rebuild a new virtual machine (this time not Ubuntu) if I cannot solve this issue.  I guess I've learned my lesson to simply dismiss Ubuntu Software Updater when it wants to update the system, at least when running in VirtualBox.  I imagine others will be running into this problem today as they update their systems; any advice in getting me back up and running would be greatly appreciated.

---

### Post by ajgreeny on 2013-09-27
You can find what the most recent updates were from command ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
``` which may give you some clues about why your problem has suddenly appeared.

---

### Post by icculus2 on 2013-09-27
That command returns the following: grep: /var/log/dpkg.log.1: No such file or directory

I was able to solve my problem by holding Shift during bootup and selecting the previous kernel version (for me it was 3.8.0-30-generic) so I think I can conclude that the upgrade updated my kernel to 3.8.0-31-generic and that VBox Guest Additions is not compatible with the newest kernel version.  I'll continue to use 3.8.0-30 for now.

---

### Post by ajgreeny on 2013-09-28
> **icculus2 said:**
> That command returns the following: grep: /var/log/dpkg.log.1: No such file or directory

I was able to solve my problem by holding Shift during bootup and selecting the previous kernel version (for me it was 3.8.0-30-generic) so I think I can conclude that the upgrade updated my kernel to 3.8.0-31-generic and that VBox Guest Additions is not compatible with the newest kernel version.  I'll continue to use 3.8.0-30 for now.

Sorry, I meant to say that you may not have a **dpkg.log.1** file and if so just look at dpkg.log, ie omit the first part of the command up to and including the &&

---

### Post by ubume2 on 2013-10-13
I have not had many problems with 13.04 (other than self-created ones). In Synaptic Package Manager completely remove the 31 kernel and then reinstall it.

If you don't have Synaptic, install it from the terminal
$sudo apt-get install synaptic

---


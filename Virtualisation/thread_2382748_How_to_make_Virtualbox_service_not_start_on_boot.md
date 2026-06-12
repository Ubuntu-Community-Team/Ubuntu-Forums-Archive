---
title: "How to make Virtualbox service not start on boot"
date: 2018-01-17
forum: Virtualisation
---

### Post by wrongusername2 on 2018-01-17
I am not sure whether virtualbox service starts **automatically** during boot time.
If it is starting automatically, can I disable that? How do I do that?
I would like to start the service manually whenever I want.


Thanks

---

### Post by cruzer001 on 2018-01-17
Its not a automatic process by default, check your startup apps.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

---

### Post by vasa1 on 2018-01-17
> **wrongusername2 said:**
> I am not sure whether virtualbox service starts **automatically** during boot time.
If it is starting automatically, can I disable that? How do I do that?
I would like to start the service manually whenever I want.


Thanks
Check *grep -i vbox /var/log/syslog* and then look at */var/log/syslog* itself for context. I don't see a way to prevent VBox stuff from starting automatically. What is your need for disabling it?

---

### Post by TheFu on 2018-01-17
[https://ubuntuforums.org/showthread.php?t=2326419](https://ubuntuforums.org/showthread.php?t=2326419) might be helpful. It explains how to enable it, so figuring out the 'disable' command shouldn't be hard.

---

### Post by vasa1 on 2018-01-17
Will it make a difference if a desktop system or a server is being used?

---

### Post by wrongusername2 on 2018-01-19
Thanks every one for responding. Sorry for delayed response. My Ubuntu machine had more critical issues so could not try the suggestions that you guys made.

```

I don't see a way to prevent VBox stuff from starting automatically. What is your need for disabling it?

```
You are right i do see vbox in sys.log
Jan 19 01:26:40 afterwindowsZBook kernel: [  748.618384] vboxdrv: 0000000000000000 VMMR0.r0
Jan 19 01:26:41 afterwindowsZBook kernel: [  748.889472] vboxdrv: 0000000000000000 VBoxDDR0.r0
Jan 19 01:26:41 afterwindowsZBook kernel: [  748.909174] vboxdrv: 0000000000000000 VBoxDD2R0.r0
Jan 19 01:28:19 afterwindowsZBook kernel: [  847.383876] vboxdrv: 0000000000000000 VMMR0.r0
Jan 19 01:28:19 afterwindowsZBook kernel: [  847.514000] vboxdrv: 0000000000000000 VBoxDDR0.r0
Jan 19 01:28:19 afterwindowsZBook kernel: [  847.514851] vboxdrv: 0000000000000000 VBoxDD2R0.r0
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.114340] vboxdrv: Found 8 processor cores
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.132123] vboxdrv: TSC mode is Invariant, tentative frequency 2693761752 Hz
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.132124] vboxdrv: Successfully loaded version 5.0.40_Ubuntu (interface 0x00240000)
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.135130] VBoxNetFlt: Successfully started.
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.137316] VBoxNetAdp: Successfully started.
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.139860] VBoxPciLinuxInit
Jan 19 12:20:38 afterwindowsZBook kernel: [  112.141392] vboxpci: IOMMU not found (not registered)

```

What is your need for disabling it?

```
 
VDI files used by VMs are kept on separate disk. These disks won't get *mounted* until I open the* File Manager Gui*. Since the disks are not mounted,  If i open *VBManager GUI*, it shows something like "....\xxxx.vdi file is missing".  I would like to avoid this error by manually starting VBservice. I know this is not a critical issue.  
Workaround is, open * File Manager Gui* before *VBManager GUI. *

```

Its not a automatic process by default, check your startup apps.

```
I do not see VB in startup. I do have SSH and Nvidia.

```

[https://ubuntuforums.org/showthread.php?t=2326419](https://ubuntuforums.org/showthread.php?t=2326419) might be helpful. It explains how to enable it, so figuring out the 'disable' command shouldn't be hard.

```
That link helped read about the way init works in Linux. As per my current knowledge of Ubuntu, those changes are too adventurous :-) For the time being I will stick to work around. My Ubuntu installation has more bigger problems(like Log-in screen loop).  So I do not like to rock the boat :-).

---

### Post by TheFu on 2018-01-19
Why not just mount the disks at boot? 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) (use this - system mounts are best)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) (has some additional information)

Waiting for an end-user to click on something seems counter productive.

---


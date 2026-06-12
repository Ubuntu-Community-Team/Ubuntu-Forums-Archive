---
title: "Ubuntu will not run on any version of vbox later than 4.2.16"
date: 2016-02-20
forum: Virtualisation
---

### Post by neemo69 on 2016-02-20
So for the last month or so I  have been trying to figure out why I've been unable to run Ubuntu on  virtualbox on my win7 host machine. Here is a video of the issue [https://www.youtube.com/watch?v=aBVwm5a863M&feature=youtu.be](https://www.youtube.com/watch?v=aBVwm5a863M&feature=youtu.be) .  After trying many older versions of virtualbox I finally found 4.2.16  to work. This problem does not matter which version of Ubuntu I've tried  (12.04,14.02,14.04,15.04,and 15.10) both 32 and 64bit. I have an AMD  FX6300 processor, ATI HD7750 video card, 8gb ram. Looking at some of the  version change logs I cant really determine what changed that could  cause this issue. Any help?

Snapshot of system:

General
Name:Ubuntu
OS Type: Ubuntu (64 bit)
System Base Memory: 5048 MB
Processor(s):6
Execution Cap: 100%
Boot Order: CD/DVD-ROM, Hard Disk
VT-x/AMD-V: Enabled
Nested Paging: Enabled
Display Video Memory: 256 MB
3D Acceleration: Enabled
2D Video Acceleration: Disabled
Remote Desktop Server: Disabled
Storage Controller: IDE
IDE Primary Master (CD/DVD): ubuntu-14.04.3-desktop-amd64.iso (1006.00 MB)
Controller: SATA
SATA Port 1: Ubuntu64.vdi (Normal, 82.04 GB)
Audio Host Driver: Windows DirectSound Controller: ICH AC97
Network Adapter 1: Intel PRO/1000 MT Desktop (Bridged adapter, Realtek PCIe GBE Family Controller)
Serial Ports
Disabled
USB Device Filters: 0 (0 active)
Shared Folders
None

---

### Post by ajgreeny on 2016-02-20
I note you have 8GB ram in the host and have allocated 5GB ram to guest.
That usually reports as an error as it is more than 50% of your host ram, though it does not stop the guest from booting when I try it on my system.  Try reducing the guest ram and see if that solves the problem for you; I suspect it won't.

I have 8GB ram in my host Xubuntu 14.04 and have allocated 4GB to my guest of Ubuntu 16.04 as I did with previous versions of *ubuntu guest OSs, and I have never had a problem like this in any version of VBox, nor in the current VBox Version 5.0.14 r105127.

---

### Post by neemo69 on 2016-02-20
No, did not help. Even took it down to 2gb.

---

### Post by MAFoElffen on 2016-02-21
Please use the following command in a commnad prmpt to fing the name of your vm:
```

VBoxManage list vms

```
Find the name of your vm and insert it into the next command:
```

VBoxManage showvminfo "PutVmNameHere"

```
Please post the results of that command... inside of code tags.

Also please post the results of
```

VBoxManage list systemproperties
VBoxManage list extpacks

```

---


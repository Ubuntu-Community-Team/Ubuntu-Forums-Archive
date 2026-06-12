---
title: "Drives only show up sometimes in Pop!_OS"
date: 2023-04-15
forum: Ubuntu/Debian BASED
---

### Post by theincrediblebungus on 2023-04-15
Drives are not mounting nor do they show up in  lsusb and they wont show  up in fdisk but other usb devices do. but  sometimes randomly the usb  devices will mount and everything is normal.
 I have updated and used the Pop recovery partition to do a refresh but  it is still doing it, also when i booted into recovery the drives would  mount.

---

### Post by TheFu on 2023-04-15
a) check the system logs.
b) look for USB connection issues.  Try a different port, different cable.  Sometimes we may have mixed a phone "charge-only" cable with a full data cable. I've done that a few times.
c) remove any hubs between the device and the computer USB port.  Some devices are sensitive when a hub is used.
d) look for power issues.  Verify that the external power to the USB device is working and sufficient. If it doesn't have one, get one.
e) not all USB devices are fully compatible with every USB controller. Some devices are known NOT to work with the chipsets in Ryzen computers, for example.

---

### Post by theincrediblebungus on 2023-04-16
so the logs dont show anything being plugged in when i plug it in and hardware issues are pretty much ruled out since i can mount drives without issue in recovery mode

---

### Post by yancek on 2023-04-16
Do all these drives have Linux filesystems on them?  Have you tried running fsck (filesystem check) on the various partitions.  If some partitions are not Linux filesystems, what are they?  If they are windows, which windows filesystem?  If ntfs, you need windows chkdsk.

---

### Post by TheFu on 2023-04-16
> **theincrediblebungus said:**
> so the logs dont show anything being plugged in when i plug it in and hardware issues are pretty much ruled out since i can mount drives without issue in recovery mode

If **dmesg** doesn't show anything when they are connected, then no electrical connection is happening over the USB port.  Try a different cable and USB port.

If the drives work when booted from a "Try Ubuntu" flash drive, but don't when booted from an installed version, then it is something about the setup and/or your personal settings.  It is possible to disable **gvfs** from working. I do this for security and performance reasons.

What do you expect to happen when the drives are plugged in?  I expect nothing except for the specific file systems I've previously setup to be mounted using **autofs**.  Many desktop users expect gvfs (as part of udisks and their file manager) to be activated and for some storage to show up in the file manager GUI.  In the file manager, that could have been disabled. How and were depends on the exact version and file manager being used.

---

### Post by theincrediblebungus on 2023-04-16
neither are working and they have been working up to this point

---

### Post by theincrediblebungus on 2023-04-16
what am i looking for in dmesg?  edit: i forgot the diff command was a thing and there is no difference between the dmesg output with the usb plugged in. so how is that fixed?

---

### Post by theincrediblebungus on 2023-04-16
> **yancek said:**
> Do all these drives have Linux filesystems on them?  Have you tried running fsck (filesystem check) on the various partitions.  If some partitions are not Linux filesystems, what are they?  If they are windows, which windows filesystem?  If ntfs, you need windows chkdsk.  neither are working between my ntfs and my ext4 drives

---

### Post by TheFu on 2023-04-16
> **theincrediblebungus said:**
> what am i looking for in dmesg?  edit: i forgot the diff command was a thing and there is no difference between the dmesg output with the usb plugged in. so how is that fixed?

[LIST=1]
[*]**dmesg -w**
[*]plug in the USB device.  Is anything shown within the 5 seconds after?
[/LIST]

If not, it is a hardware issue.

---

### Post by theincrediblebungus on 2023-04-16
> **TheFu said:**
> 
[LIST=1] 
[*]**dmesg -w** 
[*]plug in the USB device.  Is anything shown within the 5 seconds after? 
[/LIST]
  If not, it is a hardware issue.  but if its a hardware issue it shouldn't work in recovery mode

---

### Post by TheFu on 2023-04-16
> **theincrediblebungus said:**
> but if its a hardware issue it shouldn't work in recovery mode

Create a new userid, login using that. Does it work?

---

### Post by theincrediblebungus on 2023-04-16
> **TheFu said:**
> Create a new userid, login using that. Does it work?  Made a new user and logged in but still no luck

---

### Post by TheFu on 2023-04-16
> **theincrediblebungus said:**
> Made a new user and logged in but still no luck

So that means the problem is system-wide, not just 1 user.

Is the system fully patched?
```
sudo apt update
sudo apt full-upgrade
```

Maybe someone familiar with PopOS can help?

---

### Post by theincrediblebungus on 2023-04-16
> **TheFu said:**
> So that means the problem is system-wide, not just 1 user.  Is the system fully patched? ```
sudo apt update sudo apt full-upgrade
```  Maybe someone familiar with PopOS can help?  possibly, im still going to try but if it isnt working i think i will just try a fresh install

---


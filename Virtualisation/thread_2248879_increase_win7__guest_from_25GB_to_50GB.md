---
title: "increase win7  guest from 25GB to 50GB"
date: 2014-10-17
forum: Virtualisation
---

### Post by cmcanulty on 2014-10-17
I have tried several commands and am not able to do this what am I doing wrong?

```
cmcanulty@ubuntu1:~$ VBoxManage list hdds
UUID:           0504a96c-b157-40ea-aa81-62f99d1b0681
Parent UUID:    base
State:          locked write
Type:           normal (base)
Location:       /home/cmcanulty/VirtualBox VMs/Windows 7/Windows 7.vdi
Storage format: VDI
Capacity:       25600 MBytes

cmcanulty@ubuntu1:~$  VBoxManage modifyhd /var/VirtualBox/HardDisks/Windows7.vdi  --resize 50000
VBoxManage: error: Could not find file for the medium '/var/VirtualBox/HardDisks/Windows7.vdi' (VERR_FILE_NOT_FOUND)
VBoxManage: error: Details: code VBOX_E_FILE_ERROR (0x80bb0004), component Medium, interface IMedium, callee nsISupports
VBoxManage: error: Context: "OpenMedium(Bstr(pszFilenameOrUuid).raw(), enmDevType, enmAccessMode, fForceNewUuidOnOpen, pMedium.asOutParam())" at line 178 of file VBoxManageDisk.cpp
cmcanulty@ubuntu1:~$ 
```

---

### Post by TheFu on 2014-10-18
/var/VirtualBox/HardDisks/Windows7.vdi - is not where the file is.  Find it.

Oh - there it is: 
Location:       /home/cmcanulty/VirtualBox VMs/Windows 7/Windows 7.vdi

Be certain to wrap that in quotes.

---

### Post by cmcanulty on 2014-10-18
[ATTACH=CONFIG]257325[/ATTACH]Ok thanks I had tried that first then went by a posting. My mistake was using " for quotes rather than ' is that standard to use single quotes?

Whoops it appeared to succeed but when I go into VB windows 7 it still shows the drive almost full and I did fully power down the VB

```
cmcanulty@ubuntu1:~$ VBoxManage modifyhd '/home/cmcanulty/VirtualBox VMs/Windows 7/Windows 7.vdi' --resize 50000
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
cmcanulty@ubuntu1:~$ 

```

---

### Post by Elfy on 2014-10-18
You've now resized the hdd - you'll need to use the win disk tool to expand it's partition to now use the new size hdd - at least I'd guess so, extrapolated from doing similar

---

### Post by TheFu on 2014-10-18
Changing the HDD size doesn't change the size of the partitions. Fix that inside the clientOS (Windows Disk Manager).

Google found this [https://forums.virtualbox.org/viewtopic.php?f=35&t=50661](https://forums.virtualbox.org/viewtopic.php?f=35&t=50661)  with warnings about certain situations. I'd carefully review the manpage.

Or you could just create a new, larger, VM-HDD, connect it to the same VM, then use a liveCD to clone/dd/fsarchive the contents into the larger space.

Disclosure: I stopped using virtualbox about 2 yrs ago ... and never got it stable on Linux hosts.

---

### Post by cmcanulty on 2014-10-18
OK that got it thanks!

---


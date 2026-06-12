---
title: "Use Guest backup to restore Host with VirtualBox"
date: 2009-09-03
forum: Virtualisation
---

### Post by crownedzero on 2009-09-03
This may seem like a silly question; but assuming you regularly backup a VM is it possible to then restore that to the host? I looked to see if I could find something similar but I wasn't really sure what to look for.

---

### Post by jocampo on 2009-09-06
You mean the vdi files? of course you can backup that and restore it later on same or different host. Is that what your question points to?

---

### Post by bodhi.zazen on 2009-09-06
In theory it would be possible. You would back up your guest using any methog (partimage , tar, etc) and then use that image to restore to the host. 

This would most certainly work with Linux, you will have problems if you try to do this with windows as the hardware will have changed and windows will not like that.

---

### Post by crownedzero on 2009-09-09
How would you accomplish this without overwriting the important stuff?

Assuming you went from a vbox to host naturally you'd want to leave all of your system/device info as is but lets say you had a dozen apps, desktop configurations etc. that you wanted to bring over?

Is there a tutorial out there for it? I've googled it, but this seems to be one of those queries you get everything EXCEPT what you want to read about.

---

### Post by dk06 on 2009-09-09
**[Export/convert VDI -> raw image]("http://forums.virtualbox.org/viewtopic.php?f=1&t=2708&start=0&sid=d59e96950b93a6265fad9449c2f68856")**

 [http://forums.virtualbox.org/viewtopic.php?f=1&t=2708](http://forums.virtualbox.org/viewtopic.php?f=1&t=2708)

^^^This one suggests PING, it's like Ghost but Not. You can make the PING ISO and mount it to the VMs CD drive, reboot and load PING from the VMs CD drive and you have some options on how you can do it. 
(just creating an image of your disk from within the VM)
__________________________________________________________________________________
To Clone a VBox Virtual Machine:
Just shutdown the VM and copy your .vdi (virtual disk) into another directory or rename it.
If you want to copy the config files along with it, you can but it isn't necessary.

You can also clone the .vdi through the terminal:
> 
** Cloning a Virtual Disk Image **

 Virtual disk images may be cloned for use in other virtual machines using the VBoxManage command. This technique also works well for converting virtual disk images from one format to another. The syntax for the command is as follows: 
 VBoxManage clonehd *<source image file>* *<target image file>* -format *<format>*  where *<source image file>* is the virtual disk image file to be converted, *<target image file>* is the name to be used for the cloned image and *format* is the target format of the virtual disk image (RAW, VDI, VMDK or VHD).  
For example, to clone a VDI disk image named Ubuntu.vdi, naming the clone Ubuntu2.vdi, the following command is executed: 
 VBoxManage clonehd Ubuntu.vdi Ubuntu2.vdi -format VDI

VirtualBox Command Line Management Interface Version 2.1.4
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Clone hard disk created in format 'VDI'. UUID: 53deab63-0492-400b-9c8f-ad3ad3756f9d
Once the cloning process is complete (the exact duration of the process depends on the size of the original virtual disk), the cloned image will need to be added to the VirtualBox virtual media inventory using the Virtual Media Manager so that it is available for attachment to a virtual machine.
[http://www.virtuatopia.com/index.php/Understanding_and_Configuring_VirtualBox_Virtual_Hard_Disks](http://www.virtuatopia.com/index.php/Understanding_and_Configuring_VirtualBox_Virtual_Hard_Disks)

---


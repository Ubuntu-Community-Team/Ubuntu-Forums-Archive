---
title: "Can't install VBox Guest Additions to enable shared folders"
date: 2014-07-28
forum: Virtualisation
---

### Post by bulrush2 on 2014-07-28
My config:
VirtualBox 4.3.14 on Win 7
Installing Ubuntu Server 13.10 as a VM


[LIST=1]
[*]I downloaded the Oracle Extension Pack from here. [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads). This is the actual filename: [http://download.virtualbox.org/virtualbox/4.3.14/Oracle_VM_VirtualBox_Extension_Pack-4.3.14-95030.vbox-extpack](http://download.virtualbox.org/virtualbox/4.3.14/Oracle_VM_VirtualBox_Extension_Pack-4.3.14-95030.vbox-extpack) which ends with "vbox-extpack". 
[*]I started the VM, and under the Devices menu, I did "Insert Guest Additions CD Image." 
[*]I got an error "Unable to insert the virtual optical disk C:\vbox\VboxAdditions.iso into the machine mymachinename". Buttons are "Force Unmount" and "Cancel". 
[*]So what do I do with the Oracle_VM_VirtualBox_Extension_Pack-4.3.14-95030.vbox-extpack, and how do I get shared folders working? 
[/LIST]

Thanks.

---

### Post by howefield on 2014-07-28
Are you asking how to install the extension pack ?

If so, load Virtualbox and from the File menu, select preferences > extensions and click on the add package icon.

---

### Post by bulrush2 on 2014-07-28
Ok, so that part worked. I started my VM again, and now I have the Ubuntu installation screen. The helpfile didn't say anything about that. The helpfile seems pretty inaccurate. 

> Select "Mount CD/DVD-ROM" from the "Devices" menu in the virtual machine's menu  bar and then "CD/DVD-ROM image". This brings up the Virtual Media Manager  described ...

There is no "Mount CD/DVD-ROM" option on the Devices menu. 

> In the Virtual Media Manager, press the "Add" button and browse your host  file system for the VBoxGuestAdditions.iso  file:

Oh, I think my problem is my Windows host has CD autorun disabled. 


> Unless you have the Autostart feature disabled in your Windows guest, Windows  will now autostart the VirtualBox Guest Additions installation program from the  Additions ISO. If the Autostart feature has been turned off, choose VBoxWindowsAdditions.exe from the CD/DVD drive  inside the guest to start the installer.

---


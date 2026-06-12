---
title: "Problem running virtualbox"
date: 2008-02-25
forum: Virtualisation
---

### Post by Northsider on 2008-02-25
> john@john-laptop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-modules package for your kernel.

         You will not be able to start VMs until this problem is fixed.
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device
Qt WARNING: X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Qt WARNING: Failed to open device



I installed via Synaptic, and run via terminal: virtualbox.  Any ideas?

---

### Post by Dojan5 on 2008-02-26
> **Northsider said:**
> I installed via Synaptic, and run via terminal: virtualbox.  Any ideas?

I think (Im not sure) that you are missing a dependency...
But as said, i think...

---

### Post by Northsider on 2008-02-26
I gathered that much, but which one?

---

### Post by SonicSteve on 2008-02-26
What about uninstalling the OSE version from our repos and downloading the Version from the virtualbox website? They have .deb files specifically for Gutsy. Also the OSE version won't do USB. From the error it seems that you have the OSE version from ubuntu repositories.

---

### Post by Northsider on 2008-02-26
> **SonicSteve said:**
> What about ... downloading the Version from the virtualbox website?

> dpkg -i '///home/john/Desktop/virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb' ;echo RESULT=$?
(Reading database ... 120634 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_1.5.6-28266_Ubuntu_gutsy_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Setting up virtualbox (1.5.6-28266_Ubuntu_gutsy) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Configuring virtualbox
----------------------

Creating group 'vboxusers'

Users of VirtualBox must be member of that group in order to have write 
permissions to /dev/vboxdrv. Otherwise starting of VMs will not be possible.

addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Starting VirtualBox kernel module vboxdrv
   ...done.
Starting VirtualBox host networking...done.

RESULT=0
 
Thats what I got, trying it now.


EDIT: installed, but when I start the virtual machine I get this:
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 


EDIT 2:  I think I got it working.  I added permissions to user.

---

### Post by SonicSteve on 2008-02-26
EDITED I had it backwards.
The one from the virtualbox website is the regular edition. Ubuntu repositories has the open source edition. Open the program, click help and about. If your version ends in OSE it won't work with USB.

---

### Post by redunbar on 2008-02-28
Actually, you CAN use USB with VirtualBox OSE.  It's really quite easy. All you have to do is use the shared folder feature of virtualBox. This is what you do for a virtual XP in a Ubuntu host.

1. Make sure that the Guest Additions are installed. To do this, start your virtual XP system, then select Devices > Install Guest Additions. Sometimes it's a little slow, and sometimes it ignores you, but be patient or try it again if nothing happens. Once it's installed, then...

2. Set up a shared folder. You don't have to make a special folder for this in Ubuntu, you can use any existing folder, including a mounted USB drive. And you don't need to use ANY command line instructions to do it. At the top of your virtual XP window, select Devices > Shared Folders. This will bring up the Shared Folders dialog box. Click on the Add A New Shared Folder button, which is in the upper right corner of the dialog box, with a + symbol on it. This will bring up the Add Share dialog box. In the Folder Path field, enter the Ubuntu path of the folder you want to share, for example: /media/USBdrive (if you have a USB drive mounted in Ubuntu as /media/USBdrive) or whatever the path to the folder is. In the Folder Name field, put in whatever name you want to use for the share in Windows. This name doesn't have to match the Ubuntu folder name. Once these fields are filled in, click on OK to exit the Add Share box, click on OK to exit the Shared Folders box, and your shared folder is set up. Now, to access the shared folder in Windows...

3. Find My Network Places, either on the Windows desktop if you put it there, or in the Start menu. Right click on it and select Map Network Drive from the menu that comes up. This will bring up the Map Network Drive dialog box, which contains a Drive field and a Folder field. The Drive field will have a suggested drive letter already entered, but if you don't like it, you can change it. The Folder field will be blank. You can either enter the shared folder name directly in it, for example \\VBOXSVR\FolderName (where FolderName is the same name you used in the Folder Name field in step 2, or you can use the browse option to select your folder. You will find your shared folder in the VirtualBox Shared Folders folder. The browse interface is a little slow and flakey on my system, so you might have to select the one you want, then select something else, then select the one you want again before you can click on OK to get back to the Map Network Drive box. Once your folder is selected, check the Reconnect at logon box unless you want to do step 3 every time you bring up Windows. Then click on OK, and your shared folder/drive is set up. Go to My Computer and you will see it as a network drive which you can use like any other drive or folder.

---

### Post by FrankVdb on 2008-02-28
Post your question on the forum at virtualbox.com.

They will be able to help you.

---


---
title: "problem running VirtualBox on Ubuntu"
date: 2009-06-25
forum: Virtualisation
---

### Post by munishvit on 2009-06-25
Does anybody know how to share clipboard from Host (using Ubuntu 9.04) to Guest (Windows XP) on Virtual Machine 2.1.4_OSE?

I have already set General>Advanced>Shared Clipboard Settings to "Bidirectioal". Still its not working??



I have some doubt on VirtualBox. It would be great if anyone could clarify them to me:

1. When we set up guest virtual machine (such as WindowsXP) do we need to install system drivers (meant for Guest OS version)?

2. After customising Guest OS and installing all the needed software, is it possible to make backup of the files form "Hard disk folder" and "Machine Folder", in order to use them on the same system after Host OS being re-installed or on some different system? If this is possible, then it would save our time of re-customising the Guest OS!!!

[http://forums.virtualbox.org/viewtopic.php?f=7&t=19168](http://forums.virtualbox.org/viewtopic.php?f=7&t=19168)

---

### Post by Cheesemill on 2009-06-25
Have you install the VirtualBox guest additions in your Windows XP guest?
 
These provide the video/network/input drivers for your XP machine as well as providing clipboard synchronation.
 
Just go to Devices > Install Guest Additions
 
 
 
1. See above.
 
2. Yes you can.

---

### Post by munishvit on 2009-06-27
> **Cheesemill said:**
> Have you install the VirtualBox guest additions in your Windows XP guest?
 
These provide the video/network/input drivers for your XP machine as well as providing clipboard synchronation.
 
Just go to Devices > Install Guest Additions
 
 
 
1. See above.
 
2. Yes you can.

Ya I have installed it already. But still clipboard is not working as it should...:(
Does this "Guest Additions" depend on hardware??..as Drivers do.

---

### Post by kixome on 2009-06-27
as far as backing up- find the export appliance option, i think under the file menu or with nothing running press ctrl+E

also i dont think the OSE version is very good, unless you are hell bent on using only open source, goto sun.com and download virtual box non-free

---

### Post by munishvit on 2009-06-27
> **kixome said:**
> as far as backing up- find the export appliance option, i think under the file menu or with nothing running press ctrl+E

also i dont think the OSE version is very good, unless you are hell bent on using only open source, goto sun.com and download virtual box non-free

Ok. I didn't know this about OSE version. I installed it through Add/Remove. I'll try non-OSE, may be this will synchronize the clipboard.:D

---


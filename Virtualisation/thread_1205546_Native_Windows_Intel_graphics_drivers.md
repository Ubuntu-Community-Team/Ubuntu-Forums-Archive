---
title: "Native Windows Intel graphics drivers"
date: 2009-07-06
forum: Virtualisation
---

### Post by Johan-Steyn on 2009-07-06
Hi All,

I have Virtualbox 2.2.4 installed and would like to know how to install native windows drivers in Virtualbox. 

Hp G5050 notebook with graphics: Intel Corporation Mobile 945GM/GMS

The drivers provided by VB cannot handle 3D graphics & acceleration.

I have read on some threads that you could accomplish this by installing Guest additions. How would you go about doing it?

Could anybody point me in the right direction (a post / thread / howto)?

Thanks,

JS

---

### Post by Cheesemill on 2009-07-06
You cannot install native windows drivers in VirtualBox.

This is because your VM cannot see your Intel graphics **at all**.
Instead it sees a virtual graphics card that is presented to it by VirtualBox, you can get the drivers for this by installing the VirtualBox Guest Additions in your VM (the manual tells you how to do this).

Even so, VirtualBox 2 doesn't support 3D acceleration at all, you need version 3 for that.

---

### Post by tacantara on 2009-07-06
VirtualBox has a .iso file built into it that contains the Guest Additions.  To access it, open your virtual machine, and from the VB menu select Devices > Mount CD/DVD ROM > CD/DVD ROM Image.  This will open a box that will allow you to see the Guest Image file.  Select it, and the program will self-install.

Once the Guest Additions is installed, you will see a VB icon in the Windows system tray.  I don't do much with the advanced graphics, so I don't know if this will take care of that problem, but I do know that you have many more useful features by installing it.  Good luck :)

---

### Post by Johan-Steyn on 2009-07-06
Hi Guys,

Thanks for the replies.

I have installed VB guest additions and it looks like at least one of the two client WinXp applications I have, requiring higher-end graphics processing, is now running in VB (haven't tried the other yet). Excellent!

I did not know VB 3.0 was out. I will try that next! Downloading it at present.

Regards,

JS

---


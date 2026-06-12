---
title: "Can't Set Correct Resolution In Virtual Windows"
date: 2008-06-13
forum: System76 Support
---

### Post by lightnb on 2008-06-13
I'm running Windows XP in VirtualBox, on Kubuntu 8.

My screen resolution is 1440x900 and is working correctly in Linux.

Virtual Windows, though, only gives me 2 resolution choices: 800x600 and 1024x768. So the virtual machine runs in a small window.

How do I force Windows to use 1440x900 whether it wants to or not?

---

### Post by pytheas22 on 2008-06-13
Do you have guest additions installed?  You need it before you can get high screen resolutions in Windows guests.  There should be an option to install guest additions under one of the file menus of the window showing your virtual machine.

---

### Post by lightnb on 2008-06-14
> **pytheas22 said:**
> Do you have guest additions installed?  You need it before you can get high screen resolutions in Windows guests.  There should be an option to install guest additions under one of the file menus of the window showing your virtual machine.

Guest Additions are working- the icon shows up in the windows system tray, and mouse integration is functioning correctly...

---

### Post by pytheas22 on 2008-06-14
In that case I would look at the settings of the Windows virtual machine.  Make sure Windows is using the right driver for your virtual video card.  It might be defaulting to the generic driver for some reason.  Go into Device Manager and see if you can update the driver.  Also what's the name of the virtual graphics device according the Device Manager?

---

### Post by lightnb on 2008-06-14
> **pytheas22 said:**
> In that case I would look at the settings of the Windows virtual machine.  Make sure Windows is using the right driver for your virtual video card.  It might be defaulting to the generic driver for some reason.  Go into Device Manager and see if you can update the driver.  Also what's the name of the virtual graphics device according the Device Manager?

in Device Manager-> Display Adapters: "VirtualBox Graphics Adapter"

Under monitors, it says "Default Monitor". If i try to update the monitor driver, it goes back to "default monitor"

---

### Post by pytheas22 on 2008-06-14
Try putting the virtual Window in fullscreen mode (right control-f) and then tell it to automatically resize (right control-g).  Does it help?

---

### Post by lightnb on 2008-06-15
> **pytheas22 said:**
> Try putting the virtual Window in fullscreen mode (right control-f) and then tell it to automatically resize (right control-g).  Does it help?

Yes, as soon as i hit ctrl-G, the windows resolution choices changed to include 1440x900. strange....

---

### Post by pytheas22 on 2008-06-15
Yeah, I remembered that I needed to do that once to get it to go into full screen mode properly.  At least it works now.

---


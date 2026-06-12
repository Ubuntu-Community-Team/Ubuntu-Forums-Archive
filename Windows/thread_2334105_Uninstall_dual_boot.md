---
title: "Uninstall dual boot"
date: 2016-08-16
forum: Windows
---

### Post by jfloyobo on 2016-08-16
I installed Ubuntu to sort out some issues getting Windows up and running (sorry).  Now trying to uninstall and fix the booting to go straight to Windows.  I have tried bootrec /fixmbr and /fixboot in the repair command prompt and it gave me a success message but still boots GRUB when I turn on.  In the command prompt it said 

x:\sources bootrec.exe /fixmbr etc.

does this need to be something about where windows is installed i.e. c:\?  Is there other options?

---

### Post by howefield on 2016-08-16
Thread moved to the "*Windows*" sub forum.

It can be a different method depending on the version of Windows that you are trying to fix ?

---

### Post by yancek on 2016-08-16
You should have been able to do anything from an Ubuntu Live DVD or flash drive that you could do from an installed system.
Which windows are you using?  windows 8 and 10 usually are UEFI and I'm not sure those commands will work.  Did you run the commands from the Repair option on your windows installation DVD?  If you want to repair your windows bootloader, you might be better off at the microsoft support site or a windows forums

---


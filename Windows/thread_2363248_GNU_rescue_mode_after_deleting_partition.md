---
title: "GNU rescue mode after deleting partition"
date: 2017-06-07
forum: Windows
---

### Post by alexk12 on 2017-06-07
Hello! 
I have a problem. I had a dual boot setup windows 7/ Linux mint. I needed to get rid of the Linux partition so I created a system image USB but screwed up in the process. I deleted the linux partition and my USB did not work. I am stuck with GNU rescue on boot up. Is it possible to boot back into Windows with out reinstalling it completely?

---

### Post by deadflowr on 2017-06-07
Moved to *Windows*

Seems you need to fix Windows bootloader now.
If you created or have access to a Windows install or recovery disk, that would help.
You might be able to fix it with boot repair, but I'm not sure.
 [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by yancek on 2017-06-08
It seems you didn't understand how your system booted and thus did your steps backward.  If you wanted to get rid of Mint and keep windows, the last thing you do is delete the Mint partition as it has boot files on it and you were almost certainly booting both Mint and windows with the Mint bootloader.  It is possible to boot both with the windows bcdedit but it is a rather cumbersome process.

So, as suggested above, what you should have done in your scenario is to first install windows code to the MBR (if you have the default windows 7 MBR install) and reboot to verify that the windows booted and then dlelete the Mint partition.  If you do have the windows 7 installation DVD, it is a simple process of using the Repair option and typing in simple commands to repair the MBR.  If you don't have it, you should be able to find some windows software you can download to do this.

---


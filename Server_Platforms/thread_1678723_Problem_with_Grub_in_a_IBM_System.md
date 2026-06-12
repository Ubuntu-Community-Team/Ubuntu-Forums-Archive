---
title: "Problem with Grub in a IBM System"
date: 2011-01-30
forum: Server Platforms
---

### Post by topix on 2011-01-30
Hey guys!

I'm with a problem in my job, and i need to resolve this. Any help, will very appreciated.

I'm trying to install ubuntu server edition 10.04, on a ibm x3650, with RAID 1, with 2 disks SCSI, 72GB in each one.


In the installation, all steps works, with no problems, no errors, the array is identified as a raid 1, everything runs fine. So, i install the bootloader (GRUB) in thhe mbr, the installation completes, and the server goes to reboot.

The ubuntu, loads fine, the login screen is showed up (in text mode), and i can login in the system, and do whatever i want. Until the second reboot when the server is rebooted by second time, the GRUB, no loads more. No error is showed up, and only a Fu**** blinking cursor on the top left appears.

I already try to execute "grub-install /dev/sda" "update-grub"before the second reboot, because, later this, i can't do anything.

Anyone, can help-me?

Tanks in advance!

---

### Post by Rubi1200 on 2011-01-31
Hi and welcome to the forums :-)

Not sure I can help you with this problem.

But, I know that those who can will want to see the results of the boot info script.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by topix on 2011-01-31
Rubi1200, tnks for the fast reply.

I resolved the issue, the problem, was the video driver, when i forced to use the vesa driver on the boot, everything works fine.

I edited the grub boot line, using xforcevesa.

Tnks!
;)

---

### Post by Rubi1200 on 2011-01-31
Excellent! Really glad you got this sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---


---
title: "Ubuntu Server 18.04.1 LTS (Bionic Beaver) crashing on install"
date: 2018-08-08
forum: Server Platforms
---

### Post by ejach2000 on 2018-08-08
Hi, I am new to Linux and the server realm in general (so be gentle pls :(). I decided to attempt to install Ubuntu Server to my home NAS to learn the basics of Linux and server development. But, on install it crashed, below is the error log. It happened when I got past the step that had me partition my HDD to install the OS. I chose the LVM option because I didn't want to do it manually.
[[IMG]https://preview.ibb.co/gzEtBU/20180808_160633.jpg[/IMG]]("https://ibb.co/krimWU")
I will provide any additional information if necessary (kind of in a rush right now)
Thanks!

---

### Post by LHammonds on 2018-08-08
I assume you are installing from the "alternative" ISO since you mentioned choosing LVM?

I cannot tell what the problem is from that screenshot (I don't have a lot of experience installing on bare metal).  But I assume whatever the issue is, it is related to bad hardware or missing or incorrect drivers for the hardware.

The 1st thing I would do is run some diagnostics to make sure the RAM is OK and that the HDD is OK.  Once you know the hardware is not the problem, it would likely just be a driver issue.

After you verify the hardware with tests, you might also want to see if there are any BIOS upgrades available.

You can also try booting the desktop LIVE DVD just to see if you can get a desktop environment started before actually doing any installs.  If you can boot a LIVE session, you can look at the hardware and see if it loaded drivers...which to me would make me think the server install could load the drivers to since they are essentially the same...just without the desktop/software.

LHammonds

---

### Post by ejach2000 on 2018-08-08
How would you recommend running the hardware test? And how would I get a desktop environment? Is that the exit to shell thing or am I way off? How do I check if there are BIOS upgrades as well?
Sorry I am new to all of this.

---

### Post by ejach2000 on 2018-08-08
Update:
Updated BIOS successfully, tried installing it again, still got the same error. Still not sure how to run diagnostics on my RAM and/or HDD, I have the FreeNAS OS installed right now, forgot to mention that on the initial post.

---

### Post by LHammonds on 2018-08-08
[Download the Desktop ISO]("https://www.ubuntu.com/download/desktop") and burn it to DVD.  Boot your machine with it in the drive.  When prompted, tell it to "Try Ubuntu without Installing"

Reference: [Try before you install]("https://tutorials.ubuntu.com/tutorial/try-ubuntu-before-you-install#0") - This will let you boot the OS to see if it can load without hardware issues.

The same menu that presents the "Try Ubuntu without Installing" should also have options to test your HDD and RAM.

**EDIT:** Added some links.

Links related to HDD testing:

[list]
[*]Ubuntu forums: [Can I test hard drive for defects?](https://ubuntuforums.org/showthread.php?t=1343410)
[*]Ubuntu forums: [Can I run a disk check from a LiveCD?](https://ubuntuforums.org/showthread.php?t=550491)
[*]Official  Ubuntu Documentation:  [Check  your hard disk for problems](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html.en)
[/list]


Links related to RAM testing:

[list]
[*]Ask Ubuntu: [How can I check my RAM and hard drive for errors?](https://askubuntu.com/questions/14303/how-can-i-check-my-ram-and-hard-drive-for-errors)
[*]Linux Help: [How to Check Your RAM on Ubuntu 18.04](https://linuxhint.com/check-ram-ubuntu/)
[*]Official Ubuntu Documentation: [Memory Test](https://help.ubuntu.com/community/MemoryTest)
[/list]


LHammonds

---


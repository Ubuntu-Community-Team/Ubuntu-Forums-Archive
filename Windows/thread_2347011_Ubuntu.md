---
title: "Ubuntu"
date: 2016-12-20
forum: Windows
---

### Post by oblivion12 on 2016-12-20
How do I switch back to the Windows OS. I've been looking from to be able to boot into back in forth. I cant find the way to boot back into Windows.

---

### Post by lisati on 2016-12-20
Assuming you are using a "dual boot" setup, you need to access the grub menu on booting your computer. Have a look [here]("https://ubuntuforums.org/showthread.php?t=1904617") for instructions on how to do this.

---

### Post by oblivion12 on 2016-12-20
I do, thanks for the link!

---

### Post by oblivion12 on 2016-12-20
How do I do it from the Windows Boot Manager? Last time when i attempted to boot into it I got a problem saying it was broken. I had a boot problembefore with my PC shutting off.

---

### Post by lisati on 2016-12-20
If you've found the grub menu, and Windows is showing but experiencing a problem, that sounds like a question for the [Windows section]("https://ubuntuforums.org/forumdisplay.php?f=170") of the forum. Keep in mind that some of the regular volunteers here might not have used Windows for some time.

---

### Post by oblivion12 on 2016-12-20
Thanks didnt realize there was a Windows Help Section.

---

### Post by oldfred on 2016-12-20
Moved to Windows sub-forum.

Have you run this in Ubuntu:
sudo update-grub

But grub only boots working Windows and you usually need to directly boot Windows with f8 to get into its repair console, or use your Windows repair disk. Boot-Repair only can do minor fixes to Windows.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---


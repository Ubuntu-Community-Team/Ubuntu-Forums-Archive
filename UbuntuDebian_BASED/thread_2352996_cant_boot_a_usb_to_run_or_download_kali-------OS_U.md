---
title: "cant boot a usb to run or download kali-------OS Ubuntu"
date: 2017-02-17
forum: Ubuntu/Debian BASED
---

### Post by sirfunkeybut on 2017-02-17
Ive installed ubuntu as my whole system and want to use kali, at least "live", if i can. i created a bootable disk with the kali "iso". when i start the boot options it only lists ubuntu. grub does launch and list ubuntu but nothing else. my usb does pop up on the desktop but i cant boot an exe file. if thats even the way i should it. im half new to all this so im sorry if my first post isnt the greatest.

---

### Post by howefield on 2017-02-17
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by yancek on 2017-02-17
You have to set the usb to first boot priority in the BIOS.  Although it is possible to boot the iso from Grub2 on Ubuntu, you would have to manually configure that and I doubt that's what you have done.

I'm not sure where an '.exe' file fits in here.  Any file with an .exe extension will only run on a windows OS.

---

### Post by sirfunkeybut on 2017-02-19
problem solved, after reformating the usb to NTSF i was able to change the boot filter to legacy and that will boot the usb only. sorry about posting  it in the wrong place, i do apreiciate the help from this site.

---


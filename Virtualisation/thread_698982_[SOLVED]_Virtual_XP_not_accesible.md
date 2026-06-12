---
title: "[SOLVED] Virtual XP not accesible"
date: 2008-02-16
forum: Virtualisation
---

### Post by ur0b0r0 on 2008-02-16
i made a virtual machine with windows xp , and its running from and external disk ,and it ran great like 5 days and then i restarted today and it was saying "innacesible disk" and this as a error message


Could not load the settings file '/media/sdb1/virtualbox/windows xp /windows xp .xml' (VERR_OPEN_FAILED).
FATAL ERROR: An exception occurred! Type:RuntimeException, Message:The primary document entity could not be opened. Id=/media/sdb1/virtualbox/windows xp /windows xp .xml
Location: '', line 0, column 0.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

i already tryed rebooting and remounting but nothing... and erasing it is not an option

---

### Post by randy78 on 2008-02-16
> **ur0b0r0 said:**
> i made a virtual machine with windows xp , and its running from and external disk ,and it ran great like 5 days and then i restarted today and it was saying "innacesible disk" and this as a error message


Could not load the settings file '/media/sdb1/virtualbox/windows xp /windows xp .xml' (VERR_OPEN_FAILED).
FATAL ERROR: An exception occurred! Type:RuntimeException, Message:The primary document entity could not be opened. Id=/media/sdb1/virtualbox/windows xp /windows xp .xml
Location: '', line 0, column 0.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

i already tryed rebooting and remounting but nothing... and erasing it is not an option

Did the location of the virtual disk change?

---

### Post by ur0b0r0 on 2008-02-16
no, i havent moved anything...

---

### Post by randy78 on 2008-02-16
Okay, try deleting the virtualized machine (NOT the vdi disk)

Then, just make a new one and use the XP vdi when it asks what disk to use.

---

### Post by ur0b0r0 on 2008-02-17
but erasing the VM will erase all my data and work on the xp...

---

### Post by asmoore82 on 2008-02-17
is the external drive still connected and mounted?

---

### Post by randy78 on 2008-02-17
EDIT:

You may want to wait until somebody else comes to look at this thread, to make sure that the solution I have proposed is safe.

I have successfully completed this task in the past, but your results may vary and I don't want you to lose all of your hard work over a mistake.

---

### Post by randy78 on 2008-02-17
I believe the solution that I proposed will only work if you haven't taken any snapshots of the virtual disk.

I will investigate further and contact you as soon as I find something out.

Take Care

---

### Post by ur0b0r0 on 2008-02-17
Well.. i appreciate that would it be help that i copy the configuration file here or something? and by the way it has a snapshot but when it said that the machine was unaccesible i entered the disk manager and said the problem was "diferencial" so there said remove snapshot so i did but nothing changed...
btw.. the disk is mounted and on and connected, i can acces all my files and i can see the vdi and everything but i cant access it....
**EDIT**
SOLVED YAAAY 
i turned the disk off and entered virtualboxerases the registration from the disk with error and the virtual  machine, then connected the disk again and i did a new virtual machine with an existing vdi , the old one and it booted my XP
THANKS A LOT MAN!

---

### Post by randy78 on 2008-02-17
> **ur0b0r0 said:**
> Well.. i appreciate that would it be help that i copy the configuration file here or something? and by the way it has a snapshot but when it said that the machine was unaccesible i entered the disk manager and said the problem was "diferencial" so there said remove snapshot so i did but nothing changed...
btw.. the disk is mounted and on and connected, i can acces all my files and i can see the vdi and everything but i cant access it....
**EDIT**
SOLVED YAAAY 
i turned the disk off and entered virtualboxerases the registration from the disk with error and the virtual  machine, then connected the disk again and i did a new virtual machine with an existing vdi , the old one and it booted my XP
THANKS A LOT MAN!

Cool!

---


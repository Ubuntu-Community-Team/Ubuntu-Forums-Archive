---
title: "Windows 98 cannot use CD drive in VirtualBox"
date: 2008-07-04
forum: Virtualisation
---

### Post by Newuser1111 on 2008-07-04
Windows 98 cannot use the CD drive.

---

### Post by f37u5g0d on 2008-07-04
Device > Mount CD > your CD drive.

---

### Post by Newuser1111 on 2008-07-04
Didn't work.

All that's in "My Computer" is 3 1/2 Floppy(A:), 5 1/4 Floppy(B:), (C:), Printers, Control Panel, Dial-Up Networking, Scheduled Tasks.

---

### Post by Newuser1111 on 2008-07-05
Help?

---

### Post by cariboo on 2008-07-05
When you setup your win98 virtual machine did you tell it to make the cd-rom drive available to the virtual machine.

Jim

---

### Post by Newuser1111 on 2008-07-05
> **cariboo907 said:**
> When you setup your win98 virtual machine did you tell it to make the cd-rom drive available to the virtual machine.

JimIt didn't ask.
(I don't think it asked.)

---

### Post by jocko on 2008-07-05
To be able to mount a cd in your virtual machine, try this:

1. Turn off the virtual machine (suspend will not work. It has to be powered off).
2. Select the machine you want to change, click "Settings".
3. In the "CD/DVD-ROM" tab of the virtual machine settings, tick the box labelled "Mount CD/DVD-device".
4. Tick the box labelled "Host CD/DVD-device".
5. Click "OK"
6. Start up your virtual machine. Now it will have a cd-rom device.

---

### Post by Newuser1111 on 2008-07-05
Already did that, Didn't work.

---

### Post by jocko on 2008-07-05
In the bottom of the virtual machine window there are some icons showing what hardware is available to the virtual machine.
Do you see a CD icon there? If you right-click it you will get a menu, which lists your physical (and virtual) CD/DVD-rom devices.
Select the one you want the virtual machine to see.

---

### Post by Newuser1111 on 2008-07-05
> **jocko said:**
> In the bottom of the virtual machine window there are some icons showing what hardware is available to the virtual machine.
Do you see a CD icon there? If you right-click it you will get a menu, which lists your physical (and virtual) CD/DVD-rom devices.
Select the one you want the virtual machine to see.Still isn't working.

---

### Post by Newuser1111 on 2008-07-05
Help?

Or should I just move all of the files I have in 98 to XP?

---


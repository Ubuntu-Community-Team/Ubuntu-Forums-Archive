---
title: "Problem installing SAMBA4"
date: 2013-09-29
forum: Server Platforms
---

### Post by Jacob_Tennant on 2013-09-29
I am attempting to install SAMBA4 on 12.04 LTS server and when I run a test on the SAMBA4 configuration I get a strange result.

I should see this...

Sharename     Type     Comment
------------      ------    -----------
netlogon         Disk     
sysvol            Disk
IPC$               IPC       IPC Service


Instead I see this...

Sharename     Type     Comment
------------      ------    -----------
Printer$         Disk     
printer            Disk
IPC$               IPC       IPC Service

I am attempting to setup SAMBA4 to replace using Microsoft Server 2008 R2 as my COI has challenged me to do this so as to stop paying Microsoft money!

Jacob Tennant
IT Development Specialist
Pierpont Community & Technical College

---

### Post by TheFu on 2013-09-29
I don't understand the question or what you've tried. Please clarify.  Actual settings might be useful too.

---

### Post by Bucky Ball on 2013-09-29
*Thread moved to **Server Platforms**.*

***Installation & Upgrades*** is for the installation and upgrade of the OS. ;)

---

### Post by Jacob_Tennant on 2013-09-29
Never mind as for some reason this morning Samba4 is running perfectly fine.

Now I am fighting with Bind9. . .

---

### Post by Bucky Ball on 2013-09-29
A miracle! Or at least good news. 

Could you please mark the thread as solved to help others from Thread Tools at top right, please. ;)

---


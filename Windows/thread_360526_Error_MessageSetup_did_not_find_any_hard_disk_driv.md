---
title: "Error Message:Setup did not find any hard disk drives installed in your system"
date: 2007-02-13
forum: Windows
---

### Post by Ziox on 2007-02-13
Hello, again.  I really need your help with Windows now. 
 
Scenerio:
New HP Pavillion dv6000t Laptop, preinstalled with Windows Vista Home Premium
I want to install Windows XP. So I placed my legitimite Windows XP installation disc in the Optical Drive, and the setup loads.  However, when I tried to install Windows XP, the setup application produced the following output (error):
 
```
 
Error Message:Setup did not find any hard disk drives installed in your system

```
 
Does anyone know of a way to fix this error?
 
Thanks in advance.

---

### Post by insane_alien on 2007-02-13
Is it one of those new hybrid drives with the flash cache or a SATA drive? if its one of those XP might not show it up and you'll need to slipstream some drivers.

if its a PATA disk, just double check the connection. or you could pop an ubuntu disk in and check that ubuntu can see the driver.

---

### Post by Ziox on 2007-02-13
Thanks for the help.  It's solved now.  It turned out that I just needed to disable a BIOS function in order for XP to see the SATA drive.  Ubuntu managed to install without a hiccup. Wow!

---

### Post by insane_alien on 2007-02-13
YES! random rambling about things i haven't one in ages pays off! 

sorry, i seem to be in a weird mood today.

---


---
title: "Dual boot problem - Ubuntu 8.10 / WinXP"
date: 2009-01-05
forum: Windows
---

### Post by Cipher8 on 2009-01-05
Hello,
I recently installed Ubuntu 8.10 on a computer already running WinXP.  The installation was simple, Ubuntu recognized all the hardware and was running well.  The boot loader was working fine, allowing me to use Linux or WinXP.

Following the instructions found via the Ubuntu online help, I installed the kubuntu package, logged off, logged on, selected Options->Change Session, and switched to KDE.  

Since doing that, I can't log on to the WinXP install.  At the boot loader screen I select Windows, Windows loads and gets to the log on dialog, but the mouse and keyboard are utterly inactive!  Not even ctrl-alt-delete has any effect.

Any ideas on how to fix this would be greatly appreciated.

(As much as I am migrating towards Linux, I still need my WinXP up and running...)

---

### Post by ajmorris on 2009-01-05
> **Cipher8 said:**
> Hello,
I recently installed Ubuntu 8.10 on a computer already running WinXP.  The installation was simple, Ubuntu recognized all the hardware and was running well.  The boot loader was working fine, allowing me to use Linux or WinXP.

Following the instructions found via the Ubuntu online help, I installed the kubuntu package, logged off, logged on, selected Options->Change Session, and switched to KDE.  

Since doing that, I can't log on to the WinXP install.  At the boot loader screen I select Windows, Windows loads and gets to the log on dialog, but the mouse and keyboard are utterly inactive!  Not even ctrl-alt-delete has any effect.

Any ideas on how to fix this would be greatly appreciated.

(As much as I am migrating towards Linux, I still need my WinXP up and running...)

hi there,
windows is a lot harder to troubleshoot than Linux, as the Microsoft method is to give the user a non-meaningful error message, and no debug information... I dont believe linux would have (and could have for that matter) affected your windows install like this, without writing something to the ntfs partition itself, which the install of ubuntu would not have. It is for that reason, that i will report this to be moved to the windows sub-forum, as this is a windows problem :) -- Mods may not agree with me however...

Anywho, onto the issue, this could be caused by a whole range of issues, as this appears to be a standard freeze... have you tried booting into safe mode yet? as this will only load the required drivers for the system to run correctly, and not any extra ones.


AJ

---

### Post by Joeb454 on 2009-01-05
Moved to Windows Discussions as it appears that the problem is with Windows rather than Ubuntu :)

---

### Post by Cipher8 on 2009-01-05
> **ajmorris said:**
> hi there,
<snip>
Anywho, onto the issue, this could be caused by a whole range of issues, as this appears to be a standard freeze... have you tried booting into safe mode yet? as this will only load the required drivers for the system to run correctly, and not any extra ones.
AJ

Thanks for the reply, AJ.
Yesterday I was unable to boot into safe mode; I thought it was the lack of keyboard at that point, but I was probably just missing the brief window to press F8.
This morning I was able to get in to safe mode, but it was nearly a minute before the mouse and keyboard were available.
Everything appears to be working as expected again.

---


---
title: "Forgotten Administrators Password in XP..."
date: 2008-11-27
forum: Windows
---

### Post by speedwell68 on 2008-11-27
Ok, a friend of mine has just been on the phone and he has forgotten the Administrators password on his XP system.  The guy is not particually IT literate and is wondering if there is anyway to get around the fact he has lost the password.  I have suggested blowing the entire system out and begining again, but they would rather not do that.  So is there anyway of bypassing the Admin password on XP?

Thanks in advance.:D

---

### Post by damis648 on 2008-11-27
Well, I suppose easiest would be downloading the OPHCrack liveCD and try that. It uses rainbow tables to crack the password, however the provided tables are only alphanumeric, so his password cannot have any spaces or special characters. See: [http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)

Another way would be to try getting in as the SYSTEM user, and then use net user to change the password. Try OPHCrack first, and if that doesn't work we can move on.

---

### Post by bmathis on 2008-11-27
You can download [Ultimate Boot CD]("http://thepiratebay.org/torrent/3897722/Ultimate_Boot_CD_4.1.1"). burn it from a working pc, and then boot the locked ouit pc with the disc. It will boot and load a live Windows session sort of like the Ubuntu live cd. From there, look for a program in the start menu called Password Renew to either reset the password for the user account in question, or create a new administrator account.

---

### Post by Sabrage on 2008-12-01
I booted with ubcd but I can't find "password renew" in the menu?

:confused:

---

### Post by HermanAB on 2008-12-01
There are special Linux boot disks that can be used to reset Windows passwords - some Googling will find them.  

Alternatively, you can use the methods here:
[http://support.microsoft.com/kb/321305](http://support.microsoft.com/kb/321305)
[http://pubs.logicalexpressions.com/Pub0009/LPMArticle.asp?ID=305](http://pubs.logicalexpressions.com/Pub0009/LPMArticle.asp?ID=305)

---


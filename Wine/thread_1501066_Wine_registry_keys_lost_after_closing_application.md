---
title: "Wine registry keys lost after closing application"
date: 2010-06-03
forum: Wine
---

### Post by david.burlingame on 2010-06-03
While installing an application I created a custom registry key for specific video settings using regedit.  Then I closed the registry editor.  The install worked and the application launched.  Once I closed the application the installed directories were no longer on the drive.  I check the registry and the installed software keys were also no longer there.  In the interest of learning from this mistake the 1st time - please reply with advice on how to avoid this user inflicted data loss on the wine C_drive and registry.

My only theory is:
It may be related to opening the registry editor file while another program (installer) was writing to it.  If I opened it before those changes had been applied then is saved it's copy.  Then I saved my copy sans installed keys I may have essentially overwritten the file without them.  Is this what I did incorrectly?

Thanks in advance,
-David  :)

---

### Post by asdfoo on 2010-06-03
please specify which version of wine you are using, which software you installed so we can try to reproduce the problem

wine-1.2-rc2 is the latest testing release of wine

---

### Post by david.burlingame on 2010-06-04
I just reinstalled the software and won't be playing with the registry until after an install finishes next time which worked.  Package manager says:

Wine1.2             1.1.31-0ubuntu3
Wine1.2-gecko   1.0.0-0ubuntu3

---

### Post by asdfoo on 2010-06-04
The version of Wine you are using was released October 9, 2009.  Wine has released about 15 versions since, so it'd be worth testing with the newest release when you encounter problems in the future.

---

### Post by david.burlingame on 2010-06-06
Doh !

I forgot to add ppa:ubuntu-wine/ppa to the software sources after a fresh install.

Thanks :)

---


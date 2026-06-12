---
title: "running stat/transfer in WINE"
date: 2010-09-24
forum: Wine
---

### Post by beew on 2010-09-24
Hi, 

I have successfully installed stat/transfer in WINE (it seems so anyway), but when I run it I get the error message > access violation at address 005046F2 in module 'st32w.exe'. Read of address 00000000.I then ran st32w.exe in the terminal and this is what I got

> fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004
err:richedit:ReadStyleSheet skipping optional destinationPlease help. Thanks.

**EDITED**: Ok, installed Riched20 and Riched30 from winetricks and fixed the richedit error message. But the mountmgr error and the access violation error still remain.

---

### Post by beew on 2010-09-24
Hmmmm... nobody seems to be interested, BUT I figured it out myself!  I compared the wine installation of stat/transfer to the windows  XP installation at work and noticed that there are no entries for OBC Driver Mgr, MS Data Access and MS Access Driver in the Wine installation. 

So after consulting Wine HQ for common MS DLLs I installed mdac25, mdac27 and mdac28  using winetricks and problem solved!

Just have an excel data sheet transferred to SPSS format and opened it with PSPP, it worked flawlessly.  Well maybe I didn't need to install all of mdac25, mdac27 and mdac28, probably mdac25 alone would have worked.

---


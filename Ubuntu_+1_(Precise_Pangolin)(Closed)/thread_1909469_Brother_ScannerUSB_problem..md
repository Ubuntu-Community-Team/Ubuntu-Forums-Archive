---
title: "Brother Scanner/USB problem."
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kurt18947 on 2012-01-15
I'm trying to install the scanner driver for an MFC-6490CW downloaded from Brother's Linux site.  Precise carries over the install problem first evident in 11.10 putting packages in usr/Lib64 instead of usr/Lib but I fixed that.  I get the following error message:
[ATTACH]210904[/ATTACH]  
This message results when opening xsane.  SimpleScan's error message is less helpful.  It does find proper scanner model,  says that it's unable to connect but no mention of why it's unable to connect.

When I run 'lsusb' I get the following:
[ATTACH]210905[/ATTACH]

I assume the error message(s) is because the scanner software is looking on bus7;dev1 when it should be looking on Bus 1;dev6.  Does anyone have an idea how to fix this, or should I report this to Brother? Thank you in advance for any thoughts.

Edit:  The printer portion of the machine works fine in Precise but it uses different packages.

---

### Post by dino99 on 2012-01-15
have you set the driver as executable ?

[http://ubuntuforums.org/showthread.php?t=1195552](http://ubuntuforums.org/showthread.php?t=1195552)

---

### Post by kurt18947 on 2012-01-16
> **dino99 said:**
> have you set the driver as executable ?

[http://ubuntuforums.org/showthread.php?t=1195552](http://ubuntuforums.org/showthread.php?t=1195552)

If I could find it, I would :redface:. The search function and other functions in Nautilus seem to function differently in 12.04 than in earlier  releases.  I submitted an email bug report to Brother.  11.10 had - and still has - an install flaw.  Brother published a work around once 11.10 was close to release.  If this is indeed a software problem and not a user problem, I expect a fix or workaround  close to 12.04's release date.

---

### Post by dino99 on 2012-01-16
> **kurt18947 said:**
> If I could find it, I would :redface:. The search function and other functions in Nautilus seem to function differently in 12.04 than in earlier  releases.  I submitted an email bug report to Brother.  11.10 had - and still has - an install flaw.  Brother published a work around once 11.10 was close to release.  If this is indeed a software problem and not a user problem, I expect a fix or workaround  close to 12.04's release date.

Dont understand your comment as you've posted "scanner driver for an MFC-6490CW downloaded from Brother's Linux site", so you might know about it.
On the other hand reporting against cups might help to get a fix.

---

### Post by kurt18947 on 2012-01-16
> **dino99 said:**
> Dont understand your comment as you've posted "scanner driver for an MFC-6490CW downloaded from Brother's Linux site", so you might know about it.
On the other hand reporting against cups might help to get a fix.

Sorry if I wasn't clear.  I downloaded the scanner driver from Brother's site and installed it as I have in past installs.  The installation in Precise is producing the error I posted.  The same scanner driver in Oeneric had (and still has) issues installing but everything works in Oeneric once the fix is applied.  The print portion of the machine works in Precise, the problem is with scanning only.   If some USB hardware error were present I'd think the print portion would not work either.  I didn't know CUPS is involved in scanning, I thought it was printing only.  I'll look into this.  Thanks for your attention.

---


---
title: "Anti virus for server"
date: 2006-09-14
forum: Server Platforms
---

### Post by dregan on 2006-09-14
hi,

I am running postfix, courier, spamassassin, gld and would like to install a virus checker for email.

I have not been able to install ClamAV (much much grief here)!

Can anyone please reccommend a suitable anti-virus program please!

Danny

---

### Post by breuerp on 2006-09-14
Try avast (free).  For a solution that you have to pay for, try Symantec for Linux.

---

### Post by jamesr on 2006-09-14
Hi,

There is also AntiVir ( google it) , it is also free for personal use, I use the Windows edition for my older PCs and I have had no problems

---

### Post by dregan on 2006-09-14
Thank you for your reply - It seems to be for the desktop only - I would like one for my server to work with postfix.

Thankyou

---

### Post by chrisfay on 2006-09-15
> I have not been able to install ClamAV (much much grief here)!

What issues are you having with ClamAV? Did you install an interface such as amavisd-new to pass mail between Postifx and ClamAV and back?

Install amavisd-new:
[http://www.ijs.si/software/amavisd/INSTALL.txt](http://www.ijs.si/software/amavisd/INSTALL.txt)

Configure amavisd-new with Postfix:
[http://www.ijs.si/software/amavisd/README.postfix.txt](http://www.ijs.si/software/amavisd/README.postfix.txt)

Between these two documents I was able to get ClamAV scanning mail just fine....

---


---
title: "DTS access"
date: 2012-05-01
forum: Security
---

### Post by daniel.cotter on 2012-05-01
Hi all,

First, kindly let me know if there is a better, more applicable forum for this question.

I am running Ubuntu 12.04, upgraded yesterday online.

I have had trouble accessing the DTS site with my CAC card, and hoped the upgrade would magically cure the problem, but, alas, it has not.  I have Sun's version of java, which is required by DTS, rather than OpenJDK, and when I access the site, the applet starts, and then loads, but it does not proceed to load the content.

I made the mistake of deleting the security device, which is located at ```
/usr/lib/pkcs11/libcoolkeypk11.so
```, in my effort to fix the problem, and now I cannot load it again.When I try, Firefox locks up.

I run 64-bit, so I tried to install ```
/usr/lib64/pkcs11/libcoolkeypk11.so
```before I deleted the original, and it locked up then, too.  Now I can't load either without Firefox locking up.

Can anyone give me an idea what to check for to get this going again?  I have a voucher to submit, and can't get onto the site.

Thanks in advance for whatever help you can offer.

---

### Post by daniel.cotter on 2012-05-03
OK, an update:

I installed a copy of firefox-9.0.1, at the recommendation of the technician at the DTS site help desk.

Even with the older version, I cannot load a new security device (coolkey).  When I try, firefox crashes.

Does this new bit of info spark any replies?  I am desperate...

Is there maybe some latent application that is interfering, that I can disable?

Thanks

---


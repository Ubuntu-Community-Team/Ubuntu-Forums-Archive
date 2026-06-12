---
title: "snort install problem"
date: 2008-12-08
forum: Security
---

### Post by madman100 on 2008-12-08
Hi all has any one got snort working in ubuntu 8.10 the problem i have is installing the snort-mysql can any one tell me if there a work around for this problem 

Thanks
madman100

---

### Post by Kinstonian on 2008-12-08
You're going to have to be more descriptive than that. ;)  Have you tried following bodhi.zazen's [tutorial](http://ubuntuforums.org/showthread.php?t=919472)?  Exactly what error are you getting?

---

### Post by madman100 on 2008-12-08
Hi Kinstonian  thanks for the reply the problem is with the sonrt-mysql when i try too install it i get this error E: snort-mysql: subprocess post-installation script returned error exit status 6

Thanks
madman100

---

### Post by Sarmacid on 2008-12-09
I'm not sure, but I think that error is related to snort not finding the database for logging. Create the database and reinstall snort.

---

### Post by madman100 on 2008-12-09
Thanks Sarmacid will try this later i for got to say i was using 8.10 64bit version if this makes any difference 

Thanks
madman100

---

### Post by Kinstonian on 2008-12-09
Is this the problem you're experiencing?

[https://bugs.launchpad.net/ubuntu/+source/snort/+bug/222091](https://bugs.launchpad.net/ubuntu/+source/snort/+bug/222091)

---

### Post by madman100 on 2008-12-11
hi guys manage to sort out the snort problem could not get the one in the synaptic package manager to work but i have got the tar.gz one to work fowling the Ubuntu Intrusion Detection tutorial every thing went fine up to the point of logging in to the browser page i have restart snort and added it to the schedule task manager to restart every 3hours  but when logging in to  base keep getting this
 Not Found

The requested URL /base was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch Server at 127.0.0.1 Port 80

Thanks
madman100

---

### Post by Sarmacid on 2008-12-11
Did you move the base directory to /var/www/base after untarring?

What's the output of ```
find / -name "base_main.php"
```

---

### Post by madman100 on 2008-12-11
Hi Sarmacid for some reason could not get the 1.3.9 version to  work downloaded the 1.4.1 version and untar to the /var/www as i done before and now that version is working 

Thanks
Madman100

---


---
title: "How do I unblock a page on Dansgardian?"
date: 2010-01-09
forum: Security
---

### Post by Cityscape on 2010-01-09
I have Ubuntu CE 9.04 which comes with Dansgardian firewall.
Well I have a site or two that I used regularly on Windows and they are good sites. Well now that I'm using Linux, Dansgardian has been blocking them.

How do I unblock these sites (I believe it's called white listing)?

---

### Post by running_rabbit07 on 2010-01-10
> **Cityscape said:**
> I have Ubuntu CE 9.04 which comes with Dansgardian firewall.
Well I have a site or two that I used regularly on Windows and they are good sites. Well now that I'm using Linux, Dansgardian has been blocking them.

How do I unblock these sites (I believe it's called white listing)?

I have never used that program, but you can use ```
man dansgardian
``` to find the commands needed to edit the program.

---

### Post by kewlrichie on 2010-01-10
You can make an "expection" to website by adding it to /etc/dansguardian/lists/expectionsitelist (I think that's the file name, if not check for something with that naming) you will need to just add the domain no www or anything just yahoo.com then reconfigure dans by using the dansguardian -g switch to gentley reconfigure or you can use the dansguardian -r to restart the service

---

### Post by Cityscape on 2010-01-10
> **kewlrichie said:**
> You can make an "expection" to website by adding it to /etc/dansguardian/lists/expectionsitelist (I think that's the file name, if not check for something with that naming) you will need to just add the domain no www or anything just yahoo.com then reconfigure dans by using the dansguardian -g switch to gentley reconfigure or you can use the dansguardian -r to restart the service

Thank you :)
It worked very well.

---


---
title: "warning: dict_nis_init: NIS domain name not set - NIS lookups disabled"
date: 2007-02-23
forum: Server Platforms
---

### Post by huggy77 on 2007-02-23
i am getting the below error in my postfix log:
warning: dict_nis_init: NIS domain name not set - NIS lookups disabled 

i have seen some posts on other boards about disabling this in my posftx main, is there another way to fix?  What is actually happening

---

### Post by huggy77 on 2007-07-06
nothin?????

---

### Post by Mr. C. on 2007-07-06
Postfix is looking to find the valid local recipients, and your system is configured to perform lookups via NIS.

Post the contents of your /etc/nsswitch.conf file and output from postconf -n.

I'll show you what you need to change.  I presume you are not using NIS.

MrC

---

### Post by huggy77 on 2007-07-09
Mr. C,  i worked this... Thankyou for offering to help though

---


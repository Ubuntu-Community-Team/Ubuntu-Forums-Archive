---
title: "syslog logging"
date: 2012-05-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by matt_symes on 2012-05-29
Has anybody else lost syslog logging ?

```
matthew@matthew-Aspire-7540 ~ % cat /var/log/syslog   
matthew@matthew-Aspire-7540 ~ % ls -l /var/log/syslog*
-rw-r--r-- 1 root root       0 May 24 03:26 /var/log/syslog
-rw-r--r-- 1 root root 1871767 May 22 16:06 /var/log/syslog.1
-rw-r--r-- 1 root root   69238 May 16 16:54 /var/log/syslog.2.gz
-rw-r--r-- 1 root root  144647 May 14 14:58 /var/log/syslog.3.gz
-rw-r--r-- 1 root root   91694 May 14 01:29 /var/log/syslog.4.gz
-rw-r--r-- 1 root root  178316 May 13 00:18 /var/log/syslog.5.gz
-rw-r--r-- 1 root root  144543 May  8 18:47 /var/log/syslog.6.gz
-rw-r--r-- 1 root root   63855 May  7 01:24 /var/log/syslog.7.gz
matthew@matthew-Aspire-7540 ~ %
```

It does not seem to be logging anything after the last updates.

Have not looked at why yet.

---

### Post by mc4man on 2012-05-29
Working fine here, fully updated as of 17:33, main server

Edit: just to note - here the owner is syslog - , group adm

---

### Post by matt_symes on 2012-05-29
Cheers mc4man. I will look at the owner and group.

---

### Post by matt_symes on 2012-05-30
Yes was an owner/group issue. Not sure how it got changed to root though.

Thanks mc4man

---


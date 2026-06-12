---
title: "Upgrade to Ubuntu Server 10.04 Postgrey Issue"
date: 2011-06-23
forum: Server Platforms
---

### Post by emufreak on 2011-06-23
Hi everybody
 
After Upgrading to Ubuntu 10.04 Server from Ubuntu 9.10 Server postgrey doesn't work anymore. There is no Postfix Process running. In Syslog i find following error.
 
mail kernel: [ 45.233041] postgrey[619]: segfault at 6f1e3fb6 ip 00007ff0566ea720 sp 00007fff4c2284a0 error 4 in libdb-4.8.so[7ff05669a000+16a000]
 
I already reinstalled libdb, postgrey and postfix. This didn't solve the problem.
 
Does anyone have any idea what's causing this
 
Thanks

---

### Post by emufreak on 2011-06-28
No reply yet. :( Any Ideas are greatly appreciated.

---

### Post by emufreak on 2011-06-30
I just made a fresh install of Ubuntu 10.04. Now it works

---

### Post by nospamplease on 2011-09-26
I had this problem, I suspected it might be the database files so I navigated to /var/lib/postgrey and moved all the files there to another folder.  Started postgrey and it recreated the files and no more segfault.

---


---
title: "mod_proxy attempts"
date: 2007-12-08
forum: Server Platforms
---

### Post by twill30 on 2007-12-08
Hi - in our logwatch reports we see the following type of entries quite frequently (every day):

 Connection attempts using mod_proxy:                                                                                                                            
    201.244.98.185 -> proxychecker.net:80: 1 Time(s)                                                                                                             
    201.87.18.90 -> mailb.microsoft.com:25: 1 Time(s)                                                                                                            
    201.87.18.90 -> [www.google.com:443:](www.google.com:443:) 1 Time(s)

Just looking for some reassurance that these are nothing to be directly concerned about (we haven't got the mod_proxy apache module enabled) and that we don't need to take action.

Thanks!

---

### Post by MJN on 2007-12-09
If you haven't got mod_proxy enabled then you don't have anything to worry about - they were merely (unsatisfied) client requests.

Only if you do use that module would you have to ensure you are not acting as an open proxy (unless that was the intent).

Mathew

---


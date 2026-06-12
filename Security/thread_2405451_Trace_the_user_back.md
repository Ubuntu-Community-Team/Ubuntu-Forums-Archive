---
title: "Trace the user back"
date: 2018-11-06
forum: Security
---

### Post by pratikr7 on 2018-11-06
Hello Everyone, 

I have one requirement where I would like to trace the individual users using the shared account in server to do some activity. Looking into the login logs I could see the source ip however after using the shared account no such info is logged hence it is difficult to trace who is the actual users. Let me give you one scenario:

There are 3 individual users: X, Y, Z who use same common user called A to login and perform some task in server. If they login at the same time I can identify them with the source ip which will be in system logs. Once they use the common user called A and perform any tasks, then no such further information is there to identify them is logged in. So here I would like to know and find out there is any any unique identifier to trace the particular user. Something like source_ip or session id etc. 

Please help.

---

### Post by TheFu on 2018-11-06
Don't let them use a shared account to log into the server.  Shared accounts is an anti-pattern and has been for decades.

Force them to login with individual accounts, then they can use sudo to run specific tasks under the other userid, if necessary.  sudo has many capabilities beyond just elevating the euid to root. It can be configured to allow specific userids to run specific commands as other specific userids too. Then each run would be logged.

---

### Post by bashiergui on 2018-11-14
I would correlate the login logs with firewall logs. When you see a login, look at the firewall logs at that same timestamp to see what the source IP is.

---


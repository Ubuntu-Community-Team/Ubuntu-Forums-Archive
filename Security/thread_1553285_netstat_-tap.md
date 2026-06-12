---
title: "netstat -tap"
date: 2010-08-14
forum: Security
---

### Post by loosescrew on 2010-08-14
hello, I don't have a good feel for ufw or IPtables yet.Does this netstat -tap look ok ?```
joe@joe-laptop:~$ sudo netstat -tap
[sudo] password for joe: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      1488/cupsd      
tcp        0      0 *:smtp                  *:*                     LISTEN      1449/master     
tcp        0      0 joe-laptop.local:46776  yo-in-f101.1e100.ne:www TIME_WAIT   -               
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN      1488/cupsd      
 
``` I just want to make sure i'm secure. Thanks Joe

---

### Post by bodhi.zazen on 2010-08-14
That output looks bland / standard.

By default there are no signifigant listening ports, I suggest you scan from a second box on your LAN .

---

### Post by loosescrew on 2010-08-15
Thanks, bodhi.zazen. I appreciate the reply.  Joe

---


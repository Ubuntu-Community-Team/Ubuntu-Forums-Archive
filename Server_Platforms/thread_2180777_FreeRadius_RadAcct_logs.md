---
title: "FreeRadius RadAcct logs"
date: 2013-10-14
forum: Server Platforms
---

### Post by Lucas_Robb on 2013-10-14
Hello All,

I'm running a small freeradius server and I'm looking for a simple/easy way to parse some of the log files.  I have logs for every single day to show who logged in and when, what I would like to do is be able to parse all the logs to have which user logged in on which day.  At this point I think the simplest would be to combine all of the logs for a period (month, two months, six months, all logs, etc.) into one giant log file, then to have even a one line using grep, egrep, or some other tool to give the date and which users logged in.  For example:

Log Sample:
```

Sun Oct 13 00:49:08 2013
	Packet-Type = Access-Request
	User-Name = "lucas"
	EAP-Message = 0x0201000a016c75636173
	Service-Type = Framed-User
	Framed-MTU = 1420
	NAS-IP-Address = 192.168.1.1
	Message-Authenticator = 0x20b4cfac686283f73892d565783bd7cd
	EAP-Type = Identity


Sun Oct 13 13:23:44 2013
	Packet-Type = Access-Request
	User-Name = "kyle"
	EAP-Message = 0x02010009016b796c65
	Service-Type = Framed-User
	Framed-MTU = 1420
	NAS-IP-Address = 192.168.1.1
	Message-Authenticator = 0x62fe65d6ff0c853c4670d9232c6268d0
	EAP-Type = Identity


```
Output Sample:
```

Sun Oct 13 2013
User-Name = "kyle"
User-Name = "lucas"

```

---


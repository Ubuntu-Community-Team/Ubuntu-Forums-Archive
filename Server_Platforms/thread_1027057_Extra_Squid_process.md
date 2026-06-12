---
title: "Extra Squid process?"
date: 2008-12-31
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-31
There is a squid process listening on a random port with protocol udp each time I start squid and I'm not sure what it does.

I do a "ps -ef | grep squid" and get
```
	
root     22110     1  0 18:24 ?        00:00:00 /usr/sbin/squid3 -D -sYC
proxy    22113 22110  0 18:24 ?        00:00:00 (squid) -D -sYC

```
I do a "sudo netstat -tlnup | grep squid" and get 
```

tcp        0      0 10.6.7.0:3128           0.0.0.0:*               LISTEN      22113/(squid)
udp        0      0 0.0.0.0:36947           0.0.0.0:*                           22113/(squid)

```

I'm ok with the one listening on 10.6.7.0:3128, but what does the process do that's listening on 0.0.0.0:36947?

I checked syslog and found, "DNS Socket created at 0.0.0.0, port 36947, FD 8".  Is this a DNS process of some sort?  Can I disable it?  If not, is there a way for me to make it listen on a specific ip or interface instead of 0.0.0.0?

I already disabled the icp process so it doesn't show up.

---


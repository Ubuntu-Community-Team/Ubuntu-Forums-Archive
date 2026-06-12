---
title: "Ubuntu 12.04 why is my pptp server failing when encryption is turned on?"
date: 2012-12-27
forum: Server Platforms
---

### Post by heavylifting on 2012-12-27
Ok so I have setup a PPTPD server and configured it appropriately. And I accidently posted this on the Networking & Wireless forum sorry.

**Here is my pptpd-options:**

```

name pptpd
require-mschap-v2
require-mppe-128
ms-dns 8.8.8.8
ms-dns 8.8.4.4
proxyarp
nodefaultroute
debug
lock
nobsdcomp

```

**Here is my pptpd.conf:**

```

option /etc/ppp/pptpd-options
debug
logwtmp
localip 192.168.1.241
remoteip 192.168.1.234-238,192.168.1.245

```

**Here is my chap-secrets:**

```
username pptpd password  *
```


My problem is that when I turn on require-mschap-v2 and\or require-mppe-128 that the connection fails and produces the following error.

```

Dec 27 16:18:51 mmweb1 pppd[3252]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Dec 27 16:18:51 mmweb1 pppd[3252]: pptpd-logwtmp: $Version$
Dec 27 16:18:51 mmweb1 pptpd[3251]: GRE: read(fd=6,buffer=6075a0,len=8196) from PTY 
failed: status = -1 error = Input/output error, usually caused by unexpected
termination of pppd, check option syntax and pppd logs
Dec 27 16:18:51 mmweb1 pptpd[3251]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 27 16:18:51 mmweb1 pptpd[3251]: CTRL: Reaping child PPP[3252]
Dec 27 16:18:51 mmweb1 pptpd[3251]: CTRL: Client 192.168.1.240 control connection 
finished
Dec 27 16:18:51 mmweb1 pptpd[3251]: CTRL: Exiting now
Dec 27 16:18:51 mmweb1 pptpd[3075]: MGR: Reaped child 3251

```

If I turn off require-mschap-v2 and require-mppe-128 I produce the following results and the connection succeeds and starts accepting packets.

```

Dec 27 16:30:18 mmweb1 pppd[3314]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Dec 27 16:30:18 mmweb1 pppd[3314]: pptpd-logwtmp: $Version$
Dec 27 16:30:18 mmweb1 pptpd[3313]: GRE: Bad checksum from pppd.
Dec 27 16:30:18 mmweb1 pptpd[3313]: CTRL: Received PPTP Control Message (type: 15)
Dec 27 16:30:18 mmweb1 pptpd[3313]: CTRL: Got a SET LINK INFO packet with standard ACCMs

```

What I notice is that it always says that GRE: Bad checksum from pppd. It makes me wonder what exactly is messed up with GRE on the server. Please note that I am able to connection with encryption turned off so I don't think that it is my router or isp or anything else like that. Any help is greatly appreciated thanks!

I have also posted this question on [www.superuser.com](www.superuser.com) if anyone wants to receive reputation points there.

[http://superuser.com/questions/524984/how-do-i-setup-my-ubuntu-12-04-pptpd-server-properly]("http://superuser.com/questions/524984/how-do-i-setup-my-ubuntu-12-04-pptpd-server-properly")

---


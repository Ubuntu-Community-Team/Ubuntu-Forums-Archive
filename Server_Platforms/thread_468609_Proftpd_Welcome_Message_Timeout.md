---
title: "Proftpd Welcome Message Timeout"
date: 2007-06-09
forum: Server Platforms
---

### Post by scott_ttocs46 on 2007-06-09
Hi all,

      Most of my ftp clients timed out while trying to connect to my proftpd server. I upped the timeout on my client. Finally, it started working at expected speeds. I am pretty sure it is not giving a welcome message.


This is an excerpt from my proftpd.conf:

```

.......
ServerName                      "Debian"
ServerType                      standalone
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on

TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message

.......

```


This is from the client:

```

......
Status:	Disconnected from server
Status:	Connecting to 192.168.0.229 ...
Status:	Connected with 192.168.0.229. Waiting for welcome message...
.......

```

       Is welcome.msg generated? Is it suppose to be in /etc/proftpd or the directory the ftp user has access to?

Regards,
Scott

---

### Post by scott_ttocs46 on 2007-06-09
It is very slow to the point of timing out while waiting for the welcome message. Then, it works as it should.

---


---
title: "ufw: 'Apache', 'Apache Full', 'Apache Secure'"
date: 2009-07-10
forum: Security
---

### Post by memilanuk on 2009-07-10
Hello all, 

Taking some first steps with my new Ubuntu 9.04 server.  I was fixin' to open up access to http & smb for BackupPC, using ufw.

```
monte@blackbetty:~$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
  Postfix
  Postfix Submission
  Samba
monte@blackbetty:~$
```

SSH & Samba I expected.  Postfix is only there for local mail, so no external access necessary.  The 'Apache', 'Apache Full', and 'Apache Secure' got me wondering, though.

Thinking that maybe 'Apache Secure' was a ufw profile for secure (SSL) connections, I ran the following command:

```
monte@blackbetty:~$ sudo ufw app info Apache Secure
Profile: Apache
Title: Web Server
Description: Apache v2 is the next generation of the omnipresent Apache web
server.

Port:
  80/tcp
monte@blackbetty:~$
```

which seems to indicate that its going to just open up port 80, like a regular web server would use.  FWIW, running the 'ufw app info' for the other two profiles returns *exactly* the same information.

```
man ufw
```

led me to /etc/ufw/applications.d/, specifically the file 'apache2.2-common' which contained the following:

```
[Apache]
title=Web Server
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=80/tcp

[Apache Secure]
title=Web Server (HTTPS)
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=443/tcp

[Apache Full]
title=Web Server (HTTP,HTTPS)
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=80,443/tcp

```

I'm guessing from that there actually *is* some difference between the three profiles... which begs the question, 'Why does the profile reported by ufw not reflect the config file?'

Any ideas?

TIA,

Monte

---

### Post by memilanuk on 2009-07-11
Btt

---

### Post by memilanuk on 2009-11-26
See here for an informative look @ ufw...

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/comment-page-1/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/comment-page-1/)

---

### Post by bodhi.zazen on 2009-11-26
> **memilanuk said:**
> See here for an informative look @ ufw...

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/comment-page-1/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/comment-page-1/)

I was going to explain it, but I see you found my blog, thank you for referring to it.

For the benefit of others, the ufw profiles Apache , Apache Secure, and Apache Full open speicific ports.

Apache = port 80
Apache Secure = port 443
Apache Full = both port 80 and 443

IMO they should have named "Apache Secure" a bit better, https, ssl ??

You may also define custom profiles , see my blog if interested (it is easy, but beyond this post).

---

### Post by juanco on 2010-12-16
> **memilanuk said:**
> 
```
monte@blackbetty:~$ sudo ufw app Apache Secure
Profile: Apache
Title: Web Server
Description: Apache v2 is the next generation of the omnipresent Apache web
server.

Port:
  80/tcp
monte@blackbetty:~$
```


FWI, you need to enclose the app name in quotes if it contains spaces.
```
$ sudo ufw app info "Apache Secure"
Profile: Apache Secure
Title: Web Server (HTTPS)
Description: Apache v2 is the next generation of the omnipresent Apache web
server.

Port:
  443/tcp
$
```

---


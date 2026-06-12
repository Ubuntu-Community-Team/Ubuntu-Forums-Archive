---
title: "Proftpd and ipv6"
date: 2007-02-17
forum: Server Platforms
---

### Post by cyracks on 2007-02-17
Hello,

I am trying for couple of hours to make proftpd working but without success:( Proftpd installs correctly but when I try to make a connection I get

```
ftp localhost 10001
```[I]
** Feb 18 00:20:14 ironcliff proftpd[18413] domain.com (localhost[::ffff:127.0.0.1]): FTP session closed.**

[/I] That is probably because proftpd listens only on ipv6 protocol (???)
```
netstat -lnp | grep proftpd
```[I][B]tcp6       0      0 :::10001                :::*                    LISTEN     18408/proftpd: (acc
unix  2      [ ACC ]     STREAM     LISTENING     99927    18408/proftpd: (acc /var/run/proftpd/proftpd.sock[/B]

[/I]During the startup of proftpd deamon I also get the following error:[I]
**Feb 18 00:20:08 ironcliff proftpd[18408] domain.com: error setting IPV6_V6ONLY: Protocol not available**
[/I] 
I am using Edgy with proftpd 1.3.0-9
How can I make proftpd to listen also on ipv4 protocol, or which are all the compile parameters, so I can compile the package myself ?

---


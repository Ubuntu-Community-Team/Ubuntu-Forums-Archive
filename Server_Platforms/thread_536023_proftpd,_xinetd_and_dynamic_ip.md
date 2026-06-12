---
title: "proftpd, xinetd and dynamic ip"
date: 2007-08-27
forum: Server Platforms
---

### Post by panayk on 2007-08-27
Hi,

After much trying, I have managed to get proftpd to work through xinetd (at least some basic functionality).

This is my /etc/xinetd.d/proftpd

```
# default: on
# ftp server

service ftp
{
        #flag           = REUSE <--Deprecated
        disable         = no
        socket_type     = stream
        wait            = no
        user            = root
        server          = /usr/sbin/proftpd
        log_on_success  += DURATION USERID
        log_on_failure  += USERID
        nice            = 10
}
```

I have a dynamic ip address, but I have setup a dyndns.com alias, i.e. mydomain.dyndns.com

In my /etc/proftpd/proftpd.conf I have the line:

```
MasqueradeAddress        mydomain.dyndns.com
```

Normally this is not enough:

> Question: If proftpd resolves any DNS names to IP addresses when it starts up, and I am using dynamic IP addresses which change after my proftpd has started, will proftpd see my new IP addresses?
Question: Unfortunately not. ProFTPD has no easy way of handling dynamic IP addresses by itself. One way of dealing with this situation is to restart proftpd periodically, which will force it to re-parse its configuration and thus re-resolve all IP addresses.

There is also a module for proftpd that can take care of this.

However I have also read:

> If your proftpd server is running in this mode [inetd/xinetd], you do not need to worry about restarting any servers whenever changes are made to the proftpd.conf configuration file. Since proftpd is started for each new FTP session by inetd/xinetd, and part of that startup process includes reading the configuration file, any changes will be seen by any new FTP sessions once the changes are made.

Does this mean that, since I run proftpd through xinetd, I don't have to worry about my ip changing and proftpd not knowing about it?

I suppose I could just wait a few days and see, but I'd rather get an answer from someone more knowledgeable than me. Thanks.

---

### Post by a9k on 2007-08-27
> Does this mean that, since I run proftpd through xinetd, I don't have to worry about my ip changing and proftpd not knowing about it?

No worries. Xinetd will start FTP when the request comes in. If there is already FTP running, it wouldn't have to start it BUT that would mean that someone is already connected to FTP on the ip that is current with dyndns.

---


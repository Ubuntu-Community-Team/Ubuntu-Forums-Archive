---
title: "No routing in dante-server?"
date: 2007-11-23
forum: Server Platforms
---

### Post by zeroK on 2007-11-23
Hi :-)

I'm currently trying to move a Gentoo server over to Ubuntu and I have a small problem with the dante-server package. I need that server to act as a Socks5 proxy that forwards all connections to another proxy server and so on Gentoo I was able to do that using the route-block in the sockd.conf:

```
route {
    from 0.0.0.0/0 to: 0.0.0.0/0 via otherproxyhost.com port =1080
    command: connect
}
```

When I try to do that on 7.10, all I get is this error message when trying to start danted:

```
$ /etc/init.d/danted start
Starting Dante SOCKS daemon: Nov 23 21:15:51 (1195848951) danted[0]: /etc/danted.conf: error on line 21, near 'route': syntax error
Nov 23 21:15:51 (1195848951) danted[0]: sockdexit(): terminating
```

Is there some other way how I can get that kind of proxy chaining to work with the dante-server version that comes with 7.10?

Seems like the route-block was introduced with 1.1.19 nearly 2 years ago, and Ubuntu is still using 1.1.18 :-(

---


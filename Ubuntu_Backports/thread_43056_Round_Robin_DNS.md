---
title: "Round Robin DNS"
date: 2005-06-20
forum: Ubuntu Backports
---

### Post by jayc on 2005-06-20
It'd be really great if round robin DNS could be implemented so that users only had to know a single URL that could a) distribute the load and b) mirrors could be added/removed at a central location so that if one goes down or one gets added everything with automatically be balanced out.

The only thing that would really need to be changed would be mirrors would have to agree on a common path to use, because some now use /ubp, /backport-mirror, or whatever.

---

### Post by ShaneAu on 2005-06-21
[QUOTE=jayc]It'd be really great if round robin DNS could be implemented so that users only had to know a single URL that could a) distribute the load and b) mirrors could be added/removed at a central location so that if one goes down or one gets added everything with automatically be balanced out.

The only thing that would really need to be changed would be mirrors would have to agree on a common path to use, because some now use /ubp, /backport-mirror, or whatever.[/QUOTE]
 Hehe, most people wouldn't notice, but my mirror (MirrorMAX) is round robin DNS loaded over 3 servers.

[http://dnsstuff.com/tools/dnstime.ch?name=ubuntu-backports.mirrormax.net&type=A](http://dnsstuff.com/tools/dnstime.ch?name=ubuntu-backports.mirrormax.net&type=A)

But I do suppose a wider use of this would be good, it's just that I personally like to have "mirrormax" in the URL, so people know. :).

---

### Post by rnldpj on 2011-08-06
I know this is an old post. But found this url which I think will be useful for anyone who would like to setup round robin dns in ubuntu based server. 

[http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/](http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/)

> **ShaneAu said:**
> Hehe, most people wouldn't notice, but my mirror (MirrorMAX) is round robin DNS loaded over 3 servers.

[http://dnsstuff.com/tools/dnstime.ch?name=ubuntu-backports.mirrormax.net&type=A](http://dnsstuff.com/tools/dnstime.ch?name=ubuntu-backports.mirrormax.net&type=A)

But I do suppose a wider use of this would be good, it's just that I personally like to have "mirrormax" in the URL, so people know. :).

---


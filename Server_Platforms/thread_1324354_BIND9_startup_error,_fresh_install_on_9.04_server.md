---
title: "BIND9 startup error, fresh install on 9.04 server"
date: 2009-11-12
forum: Server Platforms
---

### Post by Predatorian on 2009-11-12
howdy *buntuer's,

i just recently installed BIND9, and i recieved this error when it tried to start,

```

sudo /etc/init.d/bind9 restart
* Stopping domain name service&#8230; bind9		[ok]
rndc: connect failed: 127.0.0.1#953: connection refused

*Starting domain name service&#8230; bind9
usage: named [-4|-6] [-c conffile] [-d debuglevel] [-f|-g] [-n number_of_cups]
	     [-p port] [-s] [-t chrootdir] [-u username]
	     [-m {usage|trace|record|size|mctx}]
named: extra command line arguments
						[fail]


```

not sure what i should do, or wehre i sshould start, i know it probley has something to with named, but again, no clue. thanks for any help.

---


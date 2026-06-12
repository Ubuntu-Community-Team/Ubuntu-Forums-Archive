---
title: "Adding an extra server for mail services."
date: 2009-08-05
forum: Server Platforms
---

### Post by nonexistentera on 2009-08-05
Hello.
I have one server so far for everything, web mail and other things. I am wanting to get another server for load balancing, so that if one server is too overloaded, that it will redirect to the second/third server, finding the one with the lowest load.

Im not to sure how I would do this, but while searching I remember looking over [http://www.linuxvirtualserver.org/](http://www.linuxvirtualserver.org/). Would this be the way to go.

Im a little confused on this, so any help is good.
--nonexistentera

---

### Post by giggins on 2009-08-05
I will try a give a simple sounding answer to a vague question...

I would suggest you setup an additional server, share required data using NFS (mail directories, htdocs, etc), and use [Round-Robin DNS ]("http://en.wikipedia.org/wiki/Round_robin_DNS")to make users utilize both servers.

The link you suggested utilizes virtual servers on a cluster of real servers. Seems like a great concept, but I think Ubuntu 9.04 server already offers something like this through its [cloud computing]("http://www.ubuntu.com/products/whatisubuntu/serveredition/cloud/uec") stuff. Not really sure which is better, but I've heard good things about Ubuntu's use of [Eucalyptus]("https://help.ubuntu.com/community/Eucalyptus"). Not sure if any of this is really necessary for what you're trying to achieve though.

---

### Post by nonexistentera on 2009-08-05
What one issue I am wondering about is sessions. 
What I am trying to do is allow a spread out server layout, 
1+ for apache 
1 for mysql
... and so on.

So I am wondering how to have the user request sent to the other web server if the others have to high of a load.
I guess what I am trying to do is like what Mininova has.
Like if you visit this page [http://www.mininova.org/s](http://www.mininova.org/s) it will show like (server-14) and if you refresh the page it will show (server-2).

should I have one main machine to act as a load balancer?

--nonexistentera

---

### Post by giggins on 2009-08-05
DNS is most often cached. This means that using a round-robin DNS configuration will allow sessions to continue working, because once your client machine has looked up the DNS record for [www.domain.tld](www.domain.tld), it will cache it for as long as the TTL is set for.

That said, if you want an actual load balancer for apache, you can use a seperate apache instance, and [mod_proxy_balancer]("http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html").

---


---
title: "Scaling with 2 servers"
date: 2012-11-15
forum: Server Platforms
---

### Post by tutunmayan on 2012-11-15
Hello everyone

I have a ubuntu web server (LAMP). My boss wants me to scale this server by creating a clone behind a load balancer.

Load balance is ok but I have problems with syncing. 

What is the easiest solution you suggest for such a problem?

Servers will have local mysql servers and I thing following is enough to sync;
[LIST]
[*]var/www/ directory
[*]mysql database
[*]php sessions
[/LIST]



Note: I search for a solution but in the end I am confused than ever.
Aim of scaling is not performance but high availablity.

---

### Post by thnewguy on 2012-11-15
It might depend on how up to date the two servers have to be with each other. Are you shooting for realtime duplication or would you be able to deal with a nightly sync? If the latter, then a simple mysql dump and rsync might do the trick.

---

### Post by tutunmayan on 2012-11-15
> **thnewguy said:**
> It might depend on how up to date the two servers have to be with each other. Are you shooting for realtime duplication or would you be able to deal with a nightly sync? If the latter, then a simple mysql dump and rsync might do the trick.

Almost realtime is what I am looking for. News and updates are made multiple times during a day. 

And also dont forget about the sessions :)

---

### Post by nbetham on 2012-11-15
I am by no means an expert in this field but I can at least give you a starting point. 

If you plan to scale I would suggest off-loading the data base from the web host to a master - slave cluster architecture. In that you have a master database which you do all your writes on and then a bunch of slaves which you perform all your reads from the database on, this provides redundancy for the database aspect of things. For this setup though you will need some way to redirect where specific database accesses go either through the web app or some other system because you should only do writes on the master and reads on the slaves. With regards to syncing the file systems you might want to check out DRBD here: [http://www.drbd.org](http://www.drbd.org) Its a system that is used to sync two block devices over a network. However depending on how this is setup it could introduce a more latency to the server.

If you plan on just having one server as the master and then fail over to the other as a slave you could get by with just DRBD.

---

### Post by sandyd on 2012-11-15
> **tutunmayan said:**
> Hello everyone

I have a ubuntu web server (LAMP). My boss wants me to scale this server by creating a clone behind a load balancer.

Load balance is ok but I have problems with syncing. 

What is the easiest solution you suggest for such a problem?

Servers will have local mysql servers and I thing following is enough to sync;
[LIST]
[*]var/www/ directory
[*]mysql database
[*]php sessions
[/LIST]



Note: I search for a solution but in the end I am confused than ever.
Aim of scaling is not performance but high availablity.

Easiest way -

Percona XTRADB is fully compatible with mysql, and uses galera to do a master-master sync relationship. You can install it on both servers, and sync like that.

Php sessions -store em' in memcached or something similar

/var/www - probably a NFS mount of GlusterFS

---


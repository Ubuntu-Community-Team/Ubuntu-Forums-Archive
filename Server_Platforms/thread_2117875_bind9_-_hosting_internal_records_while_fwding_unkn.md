---
title: "bind9 - hosting internal records while fwding unknown records to external resolvers"
date: 2013-02-19
forum: Server Platforms
---

### Post by bxcrx on 2013-02-19
I wish to host a zone for example.com internally, but forward all unknown queries to my external forwarders when they don't exist in the zone. 

I've tried the following:

[img]http://i48.tinypic.com/2wckxad.png[/img]

Server A - This holds both the internal, and external zone records.  The caveat is that we do not want to keep constantly updating two different zones.

Server B - This has a zone file for each internal record.  The caveat is that its a huge pain to manage hundreds of zones between master/slave servers.

Server C - This is what we would like to have.  We host only the internal records under one zone in which the bind server checks itself first and then forwards all other queries to its external forwarders.


Unbound has the functionality that I'm looking for, but I don't want to use unbound as we're a bind shop.

e.g. 

[http://www.richweb.com/node/208](http://www.richweb.com/node/208)

---

### Post by hawkmage on 2013-02-19
It is not quite what you want but with bind all can think of is to use BIND views.  Have one or two servers that are the master for all zones that all the others are slaves to.  Use an external and internal view to control what zone info the external and internal slaves get.  Once you update one master copy the changes to the other.

You will still need maintain an interna and external zone file for each zone than has both buy you would be able to do it all from a single location.

---

### Post by confusedstingray on 2013-02-24
i do what you want, by using view and acls in bind 9
tried 2 servers and it was too complicated for the small setup i have 

here is a link that i based my bind setup from, i  modified to match my ip's and server names
 
[http://www.knowplace.org/pages/howtos/split_view_with_bind_9_howto.php](http://www.knowplace.org/pages/howtos/split_view_with_bind_9_howto.php)

---


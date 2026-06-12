---
title: "bind9 questions"
date: 2009-08-06
forum: Server Platforms
---

### Post by PryGuy on 2009-08-06
Good day everyone!

I'm new to bind, so I have three newbie questions. I have a named.conf config file:

```
include "/etc/bind/rndc.key";

acl "internal" {192.168.0.0/24;};
acl "all" {internal;127.0.0.1;};

controls {
  inet 127.0.0.1 allow {localhost;} keys {"rndc-key";};
};

options {
  directory "/var/cache/bind";	
  version "not currently available";
  forwarders{195.112.96.34;195.112.96.21;};
  forward first;
  allow-transfer{"none";};
  listen-on{all;};
};

view "internal" {
  match-clients {internal;};
  // required local host domain
  zone "localhost" in{
    type master;
    file "/etc/bind/db.local";
    allow-update{none;};
  };
  // localhost reverse map
  zone "0.0.127.in-addr.arpa" in{
    type master;
    file "/etc/bind/db.127";
    allow-update{none;};
  };
  // example.org forward zone
  zone "example.org" {
    type master;
    file "/etc/bind/zones/forward/db.example.org";
    allow-update { key "rndc-key"; };
    notify yes;
  };
  // example.org reverse zone
  zone "0.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/reverse/db.example.org";
    allow-update { key "rndc-key"; };
    notify yes;
  };
  // http://archive.ubuntu.com forward zone
  zone "archive.ubuntu.com" {
    type master;
    file "/etc/bind/zones/forward/db.archive.ubuntu.com";
    allow-query{192.168.0.0/24;};
    allow-update{none;};
  };
};

view "any" {
  match-clients {any;};
  recursion yes;
  // required local host domain
  zone "localhost" in{
    type master;
    file "/etc/bind/db.local";
    allow-update{none;};
  };
  // localhost reverse map
  zone "0.0.127.in-addr.arpa" in{
    type master;
    file "/etc/bind/db.127";
    allow-update{none;};
  };
  // example.org forward zone
  zone "example.org" {
    type master;
    file "/etc/bind/zones/forward/db.example.org";
    allow-update { key "rndc-key"; };
    notify yes;
  };
  // example.org reverse zone
  zone "0.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/zones/reverse/db.example.org";
    allow-update { key "rndc-key"; };
    notify yes;
  };
};
```As you can see I have two views, the first one called "any" for both localhost and internal queries. Second called "internal" is for internal requests only. The view called 'internal' has additional zone that is used to redirect internal archive.ubuntu.com queries to server.

The questions are:
1. Do we have to have all zones on both views? Can't we just "include" one zone into another to skip copying?
2. Do I have to include 'localhost' zone in the 'internal' zone also?
3. How the 'views' order affects the way it works?

Thank you!

---

### Post by jakev383 on 2009-08-15
I know it's been a week, but I hope to answer a couple of your questions:

> 
1. Do we have to have all zones on both views? Can't we just "include" one zone into another to skip copying?

Depends on how you set your config up (no, I didn't look at yours in depth). If you create a view that matches everything, you can just put the zone file in there and only cerate views for stuff that you do not want to match anything. For example, create a view for your internal network and put the special zone files you want in that view. Then create a view for everything else (I use "external", and put the commonly shared zone fines there. It will attempt to match in the "internal" zone, and if there is no match it will move on down the list until it does match (or doesn't).

> 
2. Do I have to include 'localhost' zone in the 'internal' zone also?

I believe this is a good idea (and maybe required), especially if you have the machine answer it's own queries from the "internal" view. Both views can share 1 zone file, and now that I think about it, you can probably get by with putting the localhost zone in the view that matches everything since it will eventually get there anyway.

> 
3. How the 'views' order affects the way it works?


IIRC, they work like everything else in Linux, and use the "match & bail" method. Meaning it checks the first set of rules and if it finds a match, services it and bails (no need to look further - we already matched something, right?). Otherwise it moves on to the next set of rules, if there is a match, serve it and bail. If no match, move to the next set of rules [rinse and repeat here].

Hopefully that answers some of your questions.

---


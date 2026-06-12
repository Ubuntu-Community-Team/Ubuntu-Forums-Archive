---
title: "BIND: different record internally for same zone"
date: 2011-06-21
forum: Server Platforms
---

### Post by hewbert on 2011-06-21
Hi,

I think this is a basic task to accomplish in BIND, but for whatever reason, I'm not having any luck making it work right.

Say I have the domain "example.com"  I have a host "host.example.com" that has both an internal and external IP.

I'd like my internal hosts to see "host.example.com" using its internal IP and externals, obviously, to access via the external.

I know about views, and have them implemented.  Unfortunately, the way I have it configured currently, all other hosts on "example.com" fail to resolve internally.  Do I have to duplicate all the records for the zone?

Here's what I've got:

/etc/bind/named.conf.local:
```

...

view "internal" {
        match-clients { internals; };
        recursion yes;

        include "/etc/bind/zones.rfc1918";
        include "/etc/bind/named.conf.default-zones";

        zone "internal.locallan." {
                type master;
                notify yes;
                file "/var/cache/bind/internal/db.internal.locallan";
                allow-update { key dhcpupdate; };
                allow-transfer { slaves; };
        };

        zone "30.172.in-addr.arpa" {
                type master;
                notify yes;
                file "/var/cache/bind/internal/db.172.30";
                allow-update { key dhcpupdate; };
                allow-transfer { slaves; };
        };

        zone "example.com" {
                type master;
                file "/var/cache/bind/external/db.example.com-internal";
                allow-transfer { slaves; };
                allow-query { any; };
        };
};

view "external" {
        match-clients { any; };
        allow-recursion {
                trusted;
        };
        zone "example.com" {
                type master;
                file "/var/cache/bind/external/db.example.com";
                allow-transfer { slaves; };
        };
     
};

...

```

With this configurations, internal hosts can resolve public addresses and local addresses (e.g. internal.locallan).  However, now they've lost their ability to resolve any "example.com" records except those specifically configured in the "db.example.com-internal" file.  All I have in that zone file are the records for "example.com" that differs from what the rest of the world sees.

Hopefully I'm making sense.  Is there an easier way to pull off what I'm trying to accomplish?

Thanks.

---

### Post by hawkmage on 2011-06-21
I have always been hesitant about having overlapping match-clients in my views.  Since you have any in the "external" view you may be getting resolution from there.  try having match-clients { !internals; } instead of "any".

---

### Post by hewbert on 2011-06-21
> **hawkmage said:**
> I have always been hesitant about having overlapping match-clients in my views.  Since you have any in the "external" view you may be getting resolution from there.  try having match-clients { !internals; } instead of "any".

Thanks for the response.  However, this is providing DNS for our public domain as well, so I can't limit it to internals.

I was hoping I could just stick the two A records in the db.example.com-internal file for the two records I need to set to an internal address, but leave out everything else for example.com

---

### Post by hawkmage on 2011-06-21
No, it is not going to combine the domain zones file for all of the views that the client matches.  It picks one and uses the info in it.  I am not sure what the exact logic is that is used to pick between the multiple matching zones, it may be the first match or there may be something more complex.  

This is why I usually configure views to be exclusive so that there is only one view/domain choice available.

---

### Post by hewbert on 2011-06-22
> **hawkmage said:**
> No, it is not going to combine the domain zones file for all of the views that the client matches.  It picks one and uses the info in it.  I am not sure what the exact logic is that is used to pick between the multiple matching zones, it may be the first match or there may be something more complex.  

This is why I usually configure views to be exclusive so that there is only one view/domain choice available.

That didn't accomplish what I need, unfortunately.  In fact, I want them to overlap.  Whatever records I don't have in one of the zone files, I want to get from the other one.  Basically, the "external" zone file for "example.com" contains *all* of the public addresses.  The "internal" zone file just has a couple specified that contain internal-only addresses.

---

### Post by hawkmage on 2011-06-22
A requests cone in froma client for a record in a specific domain.  BIND looks at the client address and determines if there is a view that allows the client to access it, if there are multiple views that match it is the first one that matches is chosen.  Then it loos to see if there is a zone file that matches the domain being requested.  Then it looks at the zone file for the record being looked for.  

Any query will only return entries from one and only one zone file.  It will not look at one and then look at the other.   

You need to put all of the records you want to resolve from internal clients (external and internal) in the internal zone and only external records in the external zone.

---

### Post by HermanAB on 2011-06-23
Howdy,

What you want to do is known as a "Split Horizon DNS".

[http://www.cyberciti.biz/faq/linux-unix-bind9-named-configure-views/](http://www.cyberciti.biz/faq/linux-unix-bind9-named-configure-views/)

[http://www.zytrax.com/books/dns/ch6/](http://www.zytrax.com/books/dns/ch6/)

---

### Post by hewbert on 2011-06-23
Thanks for the replies, guys.  I've got it working, and knew *how* to make it work, but I was hoping I'd be able to have one common zone file that was "shared" among zones.

For example, if I had 50 records for a particular zone.  Internally, 5 of those records might be different than the public sees, but the rest are the same.  I was hoping I'd be able to have a simple zone file with those 5 records internally, and the rest come from the other, "public" zone.

If I have to maintain two zone files for all the records, even the common ones, that's okay.  I just didn't know if there was a cleaner way (and maybe there is).

Thanks.

---


---
title: "Can DNS answer the same IP for any domain"
date: 2010-02-11
forum: Server Platforms
---

### Post by jonrich on 2010-02-11
My test box is running 9.10 desktop,bind,dhcp,LAMP.  Everything is working good, except for one thing.  How do I configure the DNS to answer the IP of eth3 (192.168.0.2), no matter what the client asked for?  If you ask my DNS for google.com, I want it to return 192.168.0.2.  I know this can't be that hard, I just can''t figure it out.

---

### Post by volkswagner on 2010-02-11
google.com is a public address and 192.168.x.x are local addresses.  You can't have a local ip in a public dns record.  You may need to elaborate.  

Your public dns should point to your external ip address, ie: from your isp.  Then your router shall forward (port forward) requests to your servers internal ip.

---

### Post by i.r.id10t on 2010-02-11
You would need to set up zones for the various TLDs (.com, .net, etc) and use a wildcard entry.

---

### Post by jonrich on 2010-02-11
OK, that sounds like it will work. I'll try it tonight and post the results.

@volkswagner,  the purpose of the config is to force users to hit (my) apache server, NO MATTER WHAT domain they ask for. ( and I didn't want to enter 1,000,000,000,000,000 zone files )

---

### Post by jonrich on 2010-02-12
OK, it works.  Any DNS request returns the IP of the local server.

Here is how I got it to work.

FILE : /etc/bind/named.conf
options {
    directory "/var/cache/bind";
    auth-nxdomain yes;
    listen-on-v6 { 192.168.0.2; };
    listen-on { 192.168.0.2; };
};
zone "." {
    type master;
    file "/etc/bind/zone.com";
};

FILE : /etc/bind/zone.com
$TTL    604800
@    IN    SOA    . root.localhost. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@    IN    NS    .
*.    IN    A    192.168.0.2

---


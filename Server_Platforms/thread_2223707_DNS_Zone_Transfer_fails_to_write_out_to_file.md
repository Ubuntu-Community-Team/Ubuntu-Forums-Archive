---
title: "DNS Zone Transfer fails to write out to file"
date: 2014-05-12
forum: Server Platforms
---

### Post by smerkal on 2014-05-12
I set up an Ubuntu server as secondary DNS to an Infoblox Primary. When I make changes to the primary Infoblox appliance, I see it notify the secondary, the secondary performs as SOA query, a zone transfer completes but never writes out to the file. If I restart the BIND9 service on the Ubuntu server, the zone files update to current immediately. If I delete the zone file and make a change at the primary, it will re-create the zone file with current info after the notify/xfer process. It just won't update an existing zone file.

zone files are located in /var/cache/bind with permissions 644 (as created by BIND9), have tried stopping apparmor to no avail.

_syslog:_

May 12 10:14:23 uncsns1 named[16972]: client x.x.x.x#46341: received notify for zone 'bogus.us'
May 12 10:14:23 uncsns1 named[16972]: client x.x.x.x#46341: received notify for zone '10.in-addr.arpa'
May 12 10:14:23 uncsns1 named[16972]: zone bogus.us/IN: Transfer started.
May 12 10:14:23 uncsns1 named[16972]: transfer of 'bogus.us/IN' from x.x.x.x#53: connected using y.y.y.y#49067
May 12 10:14:23 uncsns1 named[16972]: zone bogus.us/IN: transferred serial 4
May 12 10:14:23 uncsns1 named[16972]: transfer of 'bogus.us/IN' from x.x.x.x#53: Transfer completed: 1 messages, 5 records, 223 bytes, 0.008 secs (27875 bytes/sec)
May 12 10:14:23 uncsns1 named[16972]: zone bogus.us/IN: sending notifies (serial 4)
May 12 10:14:23 uncsns1 named[16972]: zone 10.in-addr.arpa/IN: Transfer started.
May 12 10:14:23 uncsns1 named[16972]: transfer of '10.in-addr.arpa/IN' from x.x.x.x#53: connected using y.y.y.y#49449
May 12 10:14:23 uncsns1 named[16972]: zone 10.in-addr.arpa/IN: transferred serial 4
May 12 10:14:23 uncsns1 named[16972]: transfer of '10.in-addr.arpa/IN' from x.x.x.x#53: Transfer completed: 1 messages, 5 records, 242 bytes, 0.009 secs (26888 bytes/sec)

_zone files AFTER xfer (added A/PTR record is missing, serial number incorrect):_

root@uncsns1:~# cat /var/cache/bind/db.bogus.us
$ORIGIN .
$TTL 28800      ; 8 hours
bogus.us                IN SOA  ns1.bogus.us. bob.bogus.us. (
                                2          ; serial
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                2419200    ; expire (4 weeks)
                                15         ; minimum (15 seconds)
                                )
                        NS      ns1.bogus.us.

$ORIGIN bogus.us.
ns1                     A       10.2.1.1

root@fdsa:~# cat /var/cache/bind/db.10.in-addr.arpa 
$ORIGIN .
$TTL 28800      ; 8 hours
10.in-addr.arpa         IN SOA  ns1.bogus.us. bob.bogus.us. (
                                2          ; serial
                                10800      ; refresh (3 hours)
                                3600       ; retry (1 hour)
                                2419200    ; expire (4 weeks)
                                15         ; minimum (15 seconds)
                                )
                        NS      ns1.bogus.us.

$ORIGIN 10.in-addr.arpa.
1.1.2                   PTR     ns1.bogus.us.

---

### Post by smerkal on 2014-05-12
Update: It does write out eventally, it just takes 10 minutes to do so. Any reason for this?

---

### Post by smerkal on 2014-05-12
Final update: I solved my own problem by learning about journaling....

---


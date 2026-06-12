---
title: "Issue with bind."
date: 2011-07-16
forum: Server Platforms
---

### Post by xathras1982 on 2011-07-16
Hi,

I have two machines setup with BIND. One configured as a Master and the other as a Slave, see config below:

**MASTER:**
zone "domain.info" {
        type master;
        file "/etc/bind/zones/domain.info.db";
        allow-transfer { 0.0.187.170; };
//      also-notify { 0.0.187.170; };
        };

zone "7.226.10.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/rev.7.226.10.in-addr.arpa";
        allow-transfer { 0.0.187.170; };
};

Note, i've replaced some of the IP's with zero's

**SLAVE:**

zone "domain.info" {
        type slave;
        file "/var/cache/bind/domain.info.db";
        masters { 0.0.99.162; };
};

zone "7.266.10.in-addr.arpa" {
        type slave;
        file "/var/cache/bind/rev.7.226.10.in-addr.arpa";
        masters { 0.0.99.162; };
};

When i do a tail, I see the following in the logs:

**MASTER:**
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: zone 127.in-addr.arpa/IN: loaded serial 1
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: zone 255.in-addr.arpa/IN: loaded serial 1
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: zone domain.info/IN: loaded serial 2011050                               8
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: zone localhost/IN: loaded serial 2
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: managed-keys-zone ./IN: loaded serial 0
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: running
Jul 16 23:29:42 ip-10-226-7-138 named[5995]: zone domain.info/IN: sending notifies (ser                               ial 20110508)
Jul 16 23:32:31 ip-10-226-7-138 named[5995]: client 0.0.187.170#45243: query (cache) '                               7.266.10.in-addr.arpa/SOA/IN' denied
Jul 16 23:34:03 ip-10-226-7-138 named[5995]: client 0.0.187.170#51078: query (cache) '                               7.266.10.in-addr.arpa/SOA/IN' denied
Jul 16 23:37:48 ip-10-226-7-138 named[5995]: client 0.0.187.170#10681: query (cache) '                               7.266.10.in-addr.arpa/SOA/IN' denied


**SLAVE:**
Jul 16 23:34:03 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: refresh: unexpected rcode (REFUSED) from master 46.137.99.162#53 (source 0.0.0.0#0)
Jul 16 23:34:03 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: Transfer started.
Jul 16 23:34:03 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: got_transfer_quota: skipping zone transfer as master 0.0.99.162#53 (source 0.0.0.0#0) is unreachable (cached)
Jul 16 23:34:17 ip-10-234-213-14 named[5851]: zone domain.info/IN: refresh: skipping zone transfer as master 0.0.99.162#53 (source 0.0.0.0#0) is unreachable (cached)
Jul 16 23:37:37 ip-10-234-213-14 named[5851]: zone domain.info/IN: refresh: skipping zone transfer as master 0.0.99.162#53 (source 0.0.0.0#0) is unreachable (cached)
Jul 16 23:37:48 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: refresh: unexpected rcode (REFUSED) from master 0.0.99.162#53 (source 0.0.0.0#0)
Jul 16 23:37:48 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: Transfer started.
Jul 16 23:37:48 ip-10-234-213-14 named[5851]: zone 7.266.10.in-addr.arpa/IN: got_transfer_quota: skipping zone transfer as master 0.0.99.162#53 (source 0.0.0.0#0) is unreachable (cached)



Any ideas anyone?

---

### Post by SeijiSensei on 2011-07-16
What are these 0.0.x.y addresses?  

Is this line:

```
allow-transfer { 0.0.187.170; };
```

intended to permit 170.187/16?  If so, the directive should read:

```
allow-transfer { 170.187.0.0/16; };
```

---

### Post by xathras1982 on 2011-07-17
Hi,
 
Thanks for the comment, it wasn't that. Mr dumb @ss here forgot an entry in the reverse dns for NS2.

---


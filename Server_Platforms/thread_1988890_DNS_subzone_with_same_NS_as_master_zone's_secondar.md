---
title: "DNS subzone with same NS as master zone's secondary NS"
date: 2012-05-28
forum: Server Platforms
---

### Post by marxlv on 2012-05-28
Hi!

I have a question I would like to clarify - googling gave me nothing so I may be using wrong terms for search.
I run DNS server for domain let's call it: mydomain.cxm
```

acl ns.myotherdomain.cxm {
  1.2.3.4;
};
zone "mydomain.cxm" in {
  type master;
  file "mydomain.cxm.zone";
  allow-transfer {"ns.myotherdomain.cxm";};
};

```
Zone definition file is as follows:
```

$ORIGIN cxm.
mydomain   86400           IN      SOA     ns.mydomain.cxm. hostmaster.mydomain.cxm. (2009072301 3600 1800 604800 86400)
                        IN      NS      ns.mydomain.cxm.
                        IN      NS      ns.myotherdomain.cxm.

$origin mydomain.cxm.

mydomain.cxm.           IN      A       11.22.33.44
www                     IN      A       11.22.33.44

```
Our subdomain administrtator wants me to add a subdomain sub like this:
```

acl ns.sub.mydomain.cxm {
  22.33.44.55;
};
zone "sub.mydomain.cxm" in {
        type slave;
        masters {"ns.sub.mydomain.cxm";};
};

```
and following name servers to mydomain.cxm.zone file:
```

sub  IN  NS ns.sub.mydomain.cxm.
sub  IN  NS ns.myotherdomain.cxm.

```

Since ns.myotherdomain.cxm already is secondary NS for mydomain.cxm wouldn't it be kind of pointless and lead to some kind of loops?

--
Marx.

---


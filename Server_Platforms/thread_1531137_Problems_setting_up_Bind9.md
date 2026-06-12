---
title: "Problems setting up Bind9"
date: 2010-07-14
forum: Server Platforms
---

### Post by mmcnitt on 2010-07-14
This is my first post in the forum so please don't be too hard, i'm posting here as a last resort since i've hit every forum and youtube video of this and i still can't get it working so it's definetly a PEBKAC error.   

that being said, I'm trying to set up a Local DNS on my ubuntu box here's my goal:


Computer from example ip 10.3.3.118 can type in "atn.check.site"

DNS settings on that computer send it's request to ubuntu box example ip (172.10.20.52)

ubuntu box translates request to example ip 172.10.20.58 and sends him on his way.

here's what i have so far for my settings.


```

/etc/resolve.conf

search atn.check.site
nameserver 172.10.20.52

``````

/etc/bind/named.conf.local

zone "atn.check.site" {
       type master;
       file "/etc/bind/zones/atn.check.site.zone";
};

//The next is the reverse DNS entry.
zone "20.10.172.in-addr.arpa" {
        type master;
        file "/etc/bind/atn.check.site.local";
};

```

```

/etc/bind/zones/atn.check.site.zone

@      IN      SOA    atn.check.site. admin.atn.check.site. {

                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

@                     IN    NS       atn.check.site.
@                     IN    A         172.10.20.52
atn.check.site    IN    A         172.10.20.52


```
```

/etc/bind/zones/atn.check.site.local

@      IN      SOA    atn.check.site. admin.atn.check.site. {

                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

@                      IN    NS        atn.check.site.
@                      IN    PTR       172.10.20.52
atn.check.site     IN    A          172.10.20.52

```

Any help at all is very appreciated, i'm about ready to do something rash like install windows o_O, stop me before i jump

---

### Post by brettg on 2010-07-14
What are you trying to achieve here? Are you setting up an internet facing host for a corporate FQDN or are you just setting up internal DNS + caching for a small home or office LAN?

If you are a n00b* I expect it may be the latter. If so I would avoid bind like the plague and take a look at dnsmasq.

```
sudo apt-get install dnsmasq
```

dnsmasq is so very much easier to configure and also includes integrated DHCP so you can ping your clients via name without all the hassle involved with setting that up in bind.

See [this for more detail]("http://tuxnetworks.blogspot.com/2009/10/dhcp-and-dns-using-dnsmasq.html")

* no offence meant!

---

### Post by mmcnitt on 2010-07-15
No harm no foul, I  was able to get it working after i installed webmin, thanks though.

---


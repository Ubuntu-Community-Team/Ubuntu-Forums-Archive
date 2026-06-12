---
title: "BIND denying LAN queries"
date: 2007-07-26
forum: Server Platforms
---

### Post by Decoy on 2007-07-26
X.X.X.X - primary ns
Y.Y.Y.Y - secondary ns
Y.Y.Y.Y is also LAN server. It doesn't query lookups for 'external' zones.
```
$ cat /etc/bind/named.conf
include "/etc/bind/named.conf.options";
logging {
        category lame-servers { null; };
        category cname { null; };
};
```
```
$ cat /etc/bind/named.conf.options
acl "xfer" {
        X.X.X.X/32;
};

acl "trusted" {
        192.168.0.1/24;
        192.168.1.1/24;
        Y.Y.Y.Y/32;
        X.X.X.X/32;
        localhost;
};

acl "bogon" {
        0.0.0.0/8;
        1.0.0.0/8;
        2.0.0.0/8;
        5.0.0.0/8;
        7.0.0.0/8;
        10.0.0.0/8;
        23.0.0.0/8;
        27.0.0.0/8;
        31.0.0.0/8;
        36.0.0.0/8;
        37.0.0.0/8;
        39.0.0.0/8;
        42.0.0.0/8;
        49.0.0.0/8;
        50.0.0.0/8;
        92.0.0.0/8;
        93.0.0.0/8;
        94.0.0.0/8;
        95.0.0.0/8;
        100.0.0.0/8;
        101.0.0.0/8;
        102.0.0.0/8;
        103.0.0.0/8;
        104.0.0.0/8;
        105.0.0.0/8;
        106.0.0.0/8;
        107.0.0.0/8;
        108.0.0.0/8;
        109.0.0.0/8;
        110.0.0.0/8;
        111.0.0.0/8;
        112.0.0.0/8;
        113.0.0.0/8;
        114.0.0.0/8;
        115.0.0.0/8;
        169.254.0.0/16;
        172.16.0.0/12;
        173.0.0.0/8;
        174.0.0.0/8;
        175.0.0.0/8;
        176.0.0.0/8;
        177.0.0.0/8;
        178.0.0.0/8;
        179.0.0.0/8;
        180.0.0.0/8;
        181.0.0.0/8;
        182.0.0.0/8;
        183.0.0.0/8;
        184.0.0.0/8;
        185.0.0.0/8;
        186.0.0.0/8;
        187.0.0.0/8;
        192.0.2.0/24;
        197.0.0.0/8;
        223.0.0.0/8;
        224.0.0.0/3;
};

options {
        directory "/var/cache/bind";

        fetch-glue no;

        notify no;

        transfer-format many-answers;

        max-transfer-time-in 60;

        interface-interval 0;

        allow-transfer {
                xfer;
        };

        allow-query {
                trusted;
        };

        listen-on {
                127.0.0.1;
                192.168.0.1;
                192.168.1.1;
                Y.Y.Y.Y;
        };

        blackhole {
                bogon;
        };
};

view "internal-in" in {
        match-clients { trusted; };
        recursion yes;
        additional-from-auth yes;
        additional-from-cache yes;

        zone "." {
                type hint;
                file "/etc/bind/db.root";
        };

        zone "localhost" {
                type master;
                file "/etc/bind/db.local";
                allow-query {
                        any;
                };
                allow-transfer {
                        none;
                };
        };

        zone "127.in-addr.arpa" {
                type master;
                file "/etc/bind/db.127";
                allow-query {
                        any;
                };
                allow-transfer {
                        none;
                };
        };

        zone "0.in-addr.arpa" {
                type master;
                file "/etc/bind/db.0";
                allow-query {
                        any;
                };
                allow-transfer {
                        none;
                };
        };

        zone "255.in-addr.arpa" {
                type master;
                file "/etc/bind/db.255";
                allow-query {
                        any;
                };
                allow-transfer {
                        none;
                };
        };
};

view "external-in" in {
        match-clients { any; };
        recursion no;
        additional-from-auth no;
        additional-from-cache no;

        zone "." {
                type hint;
                file "/etc/bind/db.root";
        };

        zone "d-fens.org.ua" IN {
                type slave;
                masters {
                        X.X.X.X;
                };
                file "d-fens.org.ua.zone";
                allow-query {
                        any;
                };
        };
};

view "external-chaos" chaos {
        match-clients { any; };
        recursion no;
        zone "." {
                type hint;
                file "/dev/null";
        };

        zone "bind" {
                type master;
                file "/etc/bind/db.bind";
                allow-query {
                        trusted;
                };
                allow-transfer {
                        none;
                };
        };
};
```
DNS lookup for d-fens.org.ua from LAN workstations is OK, but for other zones it denies query.
[quote="syslog"]Jul 19 14:57:17 brain named[14532]: denied query from [192.168.0.3].2882 for "www.designet.ru" A/IN[/quote]
Any ideas?
P.S. Ubuntu 6.10, 2.6.17-11-server, bind 8.4.6-1.

---

### Post by Decoy on 2007-07-27
BTW, */etc/resolv.conf* contains my ISP's nameservers.

Looks like my local BIND think that LAN users (192.168.0.0/16) are 'external' users... :-/

---

### Post by murraymca on 2007-07-28
Hi,

I think your allow-query needs to be in the options section of named.conf, not on its own.

transfer-format many answers is the default in BIND 9 for transfers, but shouldn't that part be included per zone not in options?

If you want to perform recursive queries, don't you need to fetch glue records?

Sorry I'm not an expert, but those are a few things I would check...

All the best.

---

### Post by Mr. C. on 2007-07-28
> **Decoy said:**
> BTW, */etc/resolv.conf* contains my ISP's nameservers./

Why are you using your ISPs servers when you are running your own DNS server?  Set nameserver to your bind server's IP.

What's the point of your allow-query any statements for your internal nets, when you already allow-query trusted in options? 

MrC

---

### Post by Decoy on 2007-07-30
Hey,

I've removed allow-query any statements in 'internal view' sections and set fetch glue to yes, but nothing changed. :(
> Jul 30 09:54:28 office named[25398]: denied query from [192.168.0.5].1047 for "yahoo.com" A/IN

---

### Post by Decoy on 2007-07-30
Everything goes well only when I set allow-query all in options, but it makes my server serve as open DNS.
I'm using ipmasq for NAT.

---

### Post by murraymca on 2007-07-30
I'm pretty new so I had a bit of trouble following your configuration file - it seems very complex.

Why do you need to deny all that stuff?  Couldn't you just use allow-query {your_subnet;}; and allow-recursion {your_subnet;};

Maybe if you commented out all the other stuff, and stick with the basics (try root hints zone only) and see what happens.  You did change your /etc/resolv.conf to use the server right?  You mentioned it wouldn't do recursive, but how would you have known if you weren't using it as a resolving server?

I'm pretty sure if you have allow-recursion {your_subnet;}; it should work fine for recursive queries, you shouldn't have to specify every server on the internet.

Cheers, good luck with it :)

---

### Post by nkassi on 2007-07-30
For one thing I do believe that you need to define the default zones in all you views (you should have an external file with all those already. name.conf on the default ubuntu installs has all of those.) Also, try putting quotes around your acl names. This probably will not fix it but I've always seen it done that way so maybe it will. (match-clients { "trusted";}; )


shouldn't your subnet should be 192.168.0/24 not 192.168.0.1/24?
same for the other one. (acl "trusted" { 192.168.0/24;}; )


Just a few of my guesses.

---

### Post by murraymca on 2007-07-30
That is correct, when you use an acl name you defined earlier in another acl you need to use "talking marks"...

---

### Post by Mr. C. on 2007-07-30
> **murraymca said:**
> That is correct, when you use an acl name you defined earlier in another acl you need to use "talking marks"...

This isn't correct.  Stings only need to be double quoted when they conflict with bind's internal keywords, such as localhost, localnet, any, none, etc.  However, it is a good, safe practice to always use them.

The subnets should be 192.168.0.0/24 and 192.168.1.0/24; or use the shorter 192.168.0.0/23;

MrC

---

### Post by murraymca on 2007-07-31
Sorry, I was trying to say in reference to something like this.

define an acl called "test".

allow-query {"test"; 10.0.0.0/8;};

Is it wrong to have test in talking marks?

---

### Post by Decoy on 2007-07-31
Hey,
I need some rest... :-/
Error was in acl 'trusted' block. There's must be
```
acl "trusted" {
        192.168.0.[COLOR="Red"]**0**[/COLOR]/24;
        192.168.1.[COLOR="Red"]**0**[/COLOR]/24;
        Y.Y.Y.Y/32;
        X.X.X.X/32;
        localhost;
};

```
instead of
```
acl "trusted" {
        192.168.0.[COLOR="Red"]**1**[/COLOR]/24;
        192.168.1.[COLOR="Red"]**1**[/COLOR]/24;
        Y.Y.Y.Y/32;
        X.X.X.X/32;
        localhost;
};

```
Now it works! Thanks a lot all of you!!!

---

### Post by Mr. C. on 2007-07-31
Glad its working for you.  Credit goes to nkassi, who noticed the incorrect host IP instead of subnet range.

murraymca: no its not wrong to use double quotes (talking marks); it is safer to always use them.

MrC

---


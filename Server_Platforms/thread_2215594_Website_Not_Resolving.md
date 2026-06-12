---
title: "Website Not Resolving"
date: 2014-04-07
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-04-07
I never understood dns properly,, but I have put together a bind file and I don't know why my website does not reslve. Can someone check it and kick me? Using bind9 on ubuntu 12.04

;
; BIND data file for theeducationchannel.info
;
$TTL 14400
@      86400    IN      SOA     server11362.theeducationchannel.info. root.server11362.abc.com. (
                2008112502      ; serial, todays date+todays
                86400           ; refresh, seconds
                7200            ; retry, seconds
                3600000         ; expire, seconds
                86400 )         ; minimum, seconds

theeducationchannel.info. 86400 IN NS ns1.carbon2u.com.
theeducationchannel.info. 86400 IN NS ns2.carbon2u.com.


theeducationchannel.info. IN A 111.90.150.93

localhost.theeducationchannel.info. IN A 127.0.0.1

theeducationchannel.info. IN MX 0 theeducationchannel.info.

mail IN CNAME theeducationchannel.info.
www IN CNAME theeducationchannel.info.
ftp IN CNAME theeducationchannel.info.

---

### Post by sandyd on 2014-04-07
Your bind9 server is refusing queries
```

;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 26790

```
Make sure you are allowing queries from external IPs (i.e. allow-query { any; }; )

---

### Post by astarmathsandphysics on 2014-04-07
What is the code for that and where do I put it?
I can ping the ip but traceroute to the domain returns 
theeducationchannel.info: Name or service not known
Cannot handle "host" cmdline arg `theeducationchannel.info' on position 1 (argc 1)

---

### Post by sandyd on 2014-04-07
> **astarmathsandphysics said:**
> What is the code for that and where do I put it?
I can ping the ip but traceroute to the domain returns 
theeducationchannel.info: Name or service not known
Cannot handle "host" cmdline arg `theeducationchannel.info' on position 1 (argc 1)

a line like below should exist in your /etc/bind/named.conf.options file.
```

allow-query { any; }; 
```

Each of your zone definitions
i.e. ```

        zone "stellasmoon.com" IN {
                type master;
                allow-query { any; };
                file "/var/lib/bind/stellasmoon.com/default";
```
should have a allow-query as well - like the above example

---

### Post by astarmathsandphysics on 2014-04-09
zone "stellasmoon.com" IN {
                type master;
                allow-query { any; };
                file "/var/lib/bind/stellasmoon.com/default";

where should I insert this code?
I thought all the bind files were in /etc/bind
/var/lib/bind/ does exist but is empty

I edited the code and put it in /etc/bind/named.conf.local

Website doesnt resolve still

---

### Post by sandyd on 2014-04-09
> **astarmathsandphysics said:**
> I edited the code and put it in /etc/bind/named.conf.local

Website doesnt resolve still

that line```
allow-query { any; };
```
should be added to your zone definition - the above was an example on how it should be added

---


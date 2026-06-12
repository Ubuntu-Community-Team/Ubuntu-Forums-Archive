---
title: "Bind9 Errors..."
date: 2010-02-11
forum: Server Platforms
---

### Post by klcom on 2010-02-11
Hi! I install bind9 on Ubuntu Server 9.02.

And have some problems.

I have 3 vlans:

192.9.200.0/24  this have dns server
192.9.201.0/24
192.9.202.0/24

With the vlan 192.9.200.0/24 all work correctly and resolve lan address and internet address.

But with the other vlans only resolv lan address, with the internet address i have this errors on the log.


Feb 10 15:11:56 ns1 named[4253]: client 192.9.202.34#62718: query (cache) 'retail.sp.f-secure.com/A/IN' denied
Feb 10 15:11:56 ns1 named[4253]: client 192.9.202.34#63694: query (cache) 'retail.sp.f-secure.com/AAAA/IN' denied
Feb 10 15:12:21 ns1 named[4253]: client 192.9.202.34#62554: query (cache) 'teredo.ipv6.microsoft.com/A/IN' denied
Feb 10 15:12:56 ns1 named[4253]: client 192.9.202.34#59123: query (cache) 'retail.sp.f-secure.com/A/IN' denied
Feb 10 15:01:20 ns1 named[4119]: client 192.9.202.34#50219: query (cache) 'www.google.es/A/IN' denied

Some idea?

Thanks! :guitar:

---

### Post by ian dobson on 2010-02-11
Hi,

Are you sure you have your acl's settung correctly:-

```

 acl black-hats {
    10.0.2.0/24;
    192.168.0.0/24;
 };

 acl red-hats {
    10.0.1.0/24;
 };

 options {
    blackhole { black-hats; };
    allow-query { red-hats; };
    allow-recursion { red-hats; };
 }

```

DNS queries are only allowed from "red-hats" - 10.0.1.0/24;
Check your /etc/bind/named.conf.options config file. Maybe there's an option for allowing all your networks to do DNS queries. Something along the lines of:- 
allow-recursion { localnets; 192.168.0.0/24;}

Regards
Ian Dobson

---

### Post by klcom on 2010-02-11
Hi Ian,

Thanks for your answer, the message are solvet but....

Now can resolve internet address, but can't resolve lan address this is the answer 


Through the vlan 192.9.202.0/24 the answer is incorrect:

```

C:\Windows\System32>nslookup sametime.xxxxxxx.com
Servidor:  UnKnown
Address:  192.9.200.231

Respuesta no autoritativa:
Nombre:  sametime.xxxxxxxxxxx.com.xxxxxx.com
Address:  67.215.65.132


```

But through the vlan 192.9.200.0/24 the answer is correct:

```


#host sametime.xxxxxxxx.com
sametime.xxxxxxxx.com has address 192.9.200.230


```

Thanks! :guitar:

---


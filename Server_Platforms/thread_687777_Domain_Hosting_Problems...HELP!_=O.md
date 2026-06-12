---
title: "Domain Hosting Problems...HELP! =O"
date: 2008-02-04
forum: Server Platforms
---

### Post by .Shaun on 2008-02-04
Ok, I have my Ubuntu 7.10 Server running perfectly, and can be accessed from my external IP, as well as my LAN IP. I have been trying to configure my domain shaunsnetwork.com to it, so I added shaunsnetwork.com in /etc/bind/named.conf and also created the DB file, but when I do host shaunsnetwork.com, it only outputs mail is handled by mail.shaunsnetwork.com or something like that. Here is my DB file:

```
shaunsnetwork.com. IN SOA ns1.shaunsnetwork.com. admin.shaunsnetwork.com. (

2006081401
28800
3600
604800
38400 )

shaunsnetwork.com. IN NS ns1.shaunsnetwork.com.
IN A 65.27.97.24
mail.shaunsnetwork.com. IN MX 10 mail.shaunsnetwork.com.
shaunsnetwork.com. IN MX 10 mail.shaunsnetwork.com.

www IN A 65.27.97.24
mail IN A 65.27.97.24
ns1 IN A 65.27.97.24

```

Please help, thanks.

---

### Post by nemilar on 2008-02-05
Your domain registrar knows the correct IP address of this nameserver?

Check that this is set correctly in your registrar's control panel.

---

### Post by koenn on 2008-02-05
shaunsnetwork.com is not a host, it's a domain. 
```

:~$ host www.shaunsnetwork.com
www.shaunsnetwork.com is an alias for server1.shaunsnetwork.com.
server1.shaunsnetwork.com has address 65.27.97.24

```
and [http://www.shaunsnetwork.com](http://www.shaunsnetwork.com) works too (but your apache still needs some work)

The one strange thing is that I get "REFUSED" from 'dig', but maybe that's just me. 

The other strange thing is that the zone file you posted doesn't mention server1 or any alias records, yet host tells me www is an alias for server1 and manages to resolve the address for server1.

Are you pulling legs ?

---


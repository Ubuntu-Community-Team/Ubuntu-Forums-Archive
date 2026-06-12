---
title: "bind9 not working ( configuration )"
date: 2009-07-10
forum: Server Platforms
---

### Post by credobyte on 2009-07-10
I've followed a few tutorials on how to set up and configure bind9, but .. it's not working :(
What could be the problem ? bind9 is running and I can't find a single reason why it shouldn't.

```
dainis@credobyte:~$ nslookup cionhost.net && nslookup ns1.cionhost.net
Server:        217.199.96.2
Address:    217.199.96.2#53

Non-authoritative answer:
*** Can't find cionhost.net: No answer

Server:        217.199.96.2
Address:    217.199.96.2#53

** server can't find ns1.cionhost.net: NXDOMAIN
``````
dainis@credobyte:~$ nslookup 217.199.96.2
Server:        217.199.96.2
Address:    217.199.96.2#53

2.96.199.217.in-addr.arpa    name = ns.ipasaule.lv.
```

---

### Post by Dublee on 2009-07-10
Make sure that the authoritative name server (ns1.cionhost.net) for cionhost.net at your domain registrar has the correct IP address.

Currently, ns1.cionhost.net shows as your authoritative name server, which resolves to 94.30.182.129.  However, port TCP 53 doesn't appear to be open at that IP address.  This means one of a few things: 1) Open up TCP 53 on your firewall, 2) bind service is not running, 3) the IP address (94.30.182.129) associated to the authoritative name server is incorrect.

When I perform nslookup ns1.cionhost.net 217.199.96.2, it resolves ns1.cionhost.net to 94.30.182.129.

Server:  ns.ipasaule.lv
Address:  217.199.96.2

Non-authoritative answer:
Name:    ns1.cionhost.net
Address:  94.30.182.129

What happens when you try to perform name resolution from the bind server itself, such as nslookup ns1.cionhost.net localhost?

---

### Post by credobyte on 2009-07-10
> **Dublee said:**
> Make sure that the authoritative name server (ns1.cionhost.net) for cionhost.net at your domain registrar has the correct IP address.

Currently, ns1.cionhost.net shows as your authoritative name server, which resolves to 94.30.182.129.  However, port TCP 53 doesn't appear to be open at that IP address.  This means one of a few things: 1) Open up TCP 53 on your firewall, 2) bind service is not running, 3) the IP address (94.30.182.129) associated to the authoritative name server is incorrect.

When I perform nslookup ns1.cionhost.net 217.199.96.2, it resolves ns1.cionhost.net to 94.30.182.129.

Server:  ns.ipasaule.lv
Address:  217.199.96.2

Non-authoritative answer:
Name:    ns1.cionhost.net
Address:  94.30.182.129

What happens when you try to perform name resolution from the bind server itself, such as nslookup ns1.cionhost.net localhost?

Awesome ! You were right - 53 port was closed :) Opened & now it works like a charm !

---

### Post by Dublee on 2009-07-10
Glad to hear.  One of the things to test when troubleshooting externally accessed services is to see if it works locally or internally.  That will often help eliminate firewall issues.

---


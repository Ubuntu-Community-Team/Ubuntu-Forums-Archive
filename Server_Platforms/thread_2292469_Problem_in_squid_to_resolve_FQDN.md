---
title: "Problem in squid to resolve FQDN"
date: 2015-08-28
forum: Server Platforms
---

### Post by sergio46 on 2015-08-28
I am configuring my ACL based on FQDN hostname. My clients are using DHCP. My DHCP server updates the zone records to my DNS server. My squid box lookups the address through my DNS server.
Problem: If my client went offline, the A and PTR records will be removed from the DNS server. If I am going to "squid -k reconfigure" my squid box it cannot find the hostname and the squid`s service go to stop/waiting.
The error when I am going to "squid -k reconfigure": aclIpParseIpData: Bad host/IP: 'name_of_the_client' in 'name_of_the_client', flags=0 : (-2) Name or service not known
How can i resolve this issue?
txs!

---

### Post by SeijiSensei on 2015-08-28
So, from what I can tell, the problem concerns Squid's ability to determine the client's hostname?  

Some solutions:
1) Don't bother with reverse lookups at all.  If you're logging client hostnames, with "log_fqdn on", then turn that off.  If clients have long leases, you can always run lookups after the fact if you need to.  At one client site, I wrote a script to parse each night's access log and store the results in a PostgreSQL database; the script does the reverse lookups.  

2) How long are the DHCP leases?  Unless you have more clients than available leases, I'd just give the leases long lifespans like months or even a year.  Would that keep the DHCP server from dropping the records?  Otherwise, you can use long leases and a static database for DNS rather than having the DHCP server update the DNS.

3) Alternatively, you can populate the /etc/hosts file on the Squid server with the list of client IPs and hostnames.  Again, with long leases, this shouldn't change all that often.

---

### Post by sergio46 on 2015-08-28
tanks for the reply.
My DHCP service is over Windows 2003.
Sorry, but i cant change the [COLOR=#000000]lifespans.
[/COLOR]Is there any way to skip squid acl records that have no associated dns record?

---

### Post by SeijiSensei on 2015-08-28
Are you using ACLs to control which clients can connect to the proxy?  If so, write your ACLs with IP addresses.
```
acl ALLOWED_CLIENTS src 10.10.10.0/24
http_access allow ALLOWED_CLIENTS

```

---

### Post by sergio46 on 2015-08-28
this maybe is a posible solution... but i have 100 clients and the ip´s may change depends what server dhcp response the request.
and i have one ACL per department, and each department have an acces list (i use squidguard to use blacklists filters)
if the ip in the ACL is wrong, squidguard fails...

---

### Post by SeijiSensei on 2015-08-28
I really think your best bet is to work with whoever administers the AD server(s) and see if you can increase the lease times.  There is no good reason to have short leases on networks where the number of client machines is smaller than the number of available IPs.  A 100-client network requires fewer than half of the 253 available addresses in a class-C subnet.  DHCP is a convenient solution for enabling quick setup of new machines, but established clients should get the same address every day.  Otherwise you'll never know for sure who is doing what.

---

### Post by sergio46 on 2015-08-31
I increase lease times to 15 days (before was in 7 days) and i will see how it works...
many thanks for your time

---

### Post by SeijiSensei on 2015-08-31
That's still rather short.  I'd give them six months or even a year myself, unless you have a network where machines are being added and removed all the time.

---


---
title: "configure www in DNS zone to be fetched from gateway"
date: 2010-01-10
forum: Server Platforms
---

### Post by tarekeldeeb on 2010-01-10
Hello all,

I've been searching for a clue to my problem.
I successfully configured my local DNS server. I have server1.mydomain.com, pc1.mydomain.com and so on ..

The problem is that my website is hosted on an external server (not on the local network), so [www.mydomain.com](www.mydomain.com) is not found in the configured zone/subnet

How can I tweak my DNS to fetch ALL subdomains from the gateway (just as it went before the DNS existed)?

Please help!

---

### Post by noway2 on 2010-01-10
I had to read this post a couple of times and I am still not sure I fully understand what you are asking, but I suspect that you may have committed a mistake with regards to the DNS.  Please clarify, do you have a publicly addressable site, hosted by a provider for "mydomain.com" AND have a publicly addressable set of servers at different addresses that you are attempting to make sub domains of "mydomain.com"?  It sounds like you are running into a problem where you are attempting to locate two locations by the same domain.

If so, the only way I can think of to make this work is to have a DNS at the location of "mydomain.com" direct the query to the location of the sub-domain.

---

### Post by tarekeldeeb on 2010-01-11
> **noway2 said:**
>  Please clarify, do you have a publicly addressable site, hosted by a provider for "mydomain.com" AND have a publicly addressable set of servers at different addresses that you are attempting to make sub domains of "mydomain.com"?

First, thank you for your reply and help :)

I shall clarify: No I have a single publicly addressable server (hosted at 1and1.com as I remember), this has some subdomains; www, webmail .. etc.

I also have a local ethernet network having some local servers and clients, they are all not publicly addressable. From my local network, I setup a DNS server to point out local machines such as server1.mydomain.com

Now the problem is:
-Local machines can access local servers, but cannot reach the public server. Ie. cannot reach [www.mydomain.com](www.mydomain.com), webmail.mydomain.com .. etc.

Is there a wildcard in the DNS config:

*OTHERS*    A    GO ASK MY GATEWAY

so I can put such line to solve my problem?

---

### Post by noway2 on 2010-01-11
Ok, I think I understand.  Your local network, can't access internet sites. at least for your server.  Are you have a problem with ALL internet sites, e.g. google.com, or just your public server?

When a server is on a different zone, subnet, network, etc, the query will be routed to the gateway.  If it is all sites that are causing problem, you probably have a network configuration problem.  Possibilities include not have a gateway defined (DHCP setup) or a DNS setup problem such as the ability for the DNS to query beyond itself. 

In either case, the next step will be to run some simple tests from the local network.
1 - try to ping [www.mydomain.com](www.mydomain.com).
2 - if this doesn't work, try to ping it via its IP address
3 - do an nslookup on [www.mydomain.com](www.mydomain.com).  Is the name server able to resolve it?
4 - try traceroute to [www.mydomain.com](www.mydomain.com).  This will show you where in the LAN -> internet you are getting to.

Please run the above tests and if you still have trouble, post the results.  Perhaps this will tell us what is happening.

---

### Post by tarekeldeeb on 2010-01-11
> **noway2 said:**
>  Are you have a problem with ALL internet sites, e.g. google.com, or just your public server?


Thank you for helping ..

yes All internet sites are accessible, they do not fall in mydomain.com zone!

The problem is only with mydomain.com site.
I cannot ping by name, but pings by public IP

---

### Post by koenn on 2010-01-11
You can't just add that (non-local) server's IP address in the zone file ?

---

### Post by noway2 on 2010-01-12
One of the steps when you registered your hosted domain would have been to have the IP registered with the root DNS server for the base domain (.com., .net., etc).  The IP address will then propagate across the world to the other key DNS servers and so forth.  In any advent, if it is properly registered, a DNS query will go back to the root server if needed to get the next step and proceed to work recursively until the IP is found.

This is looking like there is a problem with the DNS setting your LAN is using - OR - something is blocking access to the site.

In my last post, I suggested some tests to run.  They will give you more information as to why you can't access the site.

---


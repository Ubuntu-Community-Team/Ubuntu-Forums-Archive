---
title: "Setting up my own dynamic IP forwarding service - alternative to DynDns"
date: 2013-06-12
forum: Server Platforms
---

### Post by garbage98 on 2013-06-12
Hi folks,

I'm pretty new here, so please give me some credit in advance.

Here is my scenario:

I have rented a small virtual server from one of these hosting companies running ubuntu server precise. This server has a static IP address and serves some web pages on different domains with the apache server. As far as good.

In addition I have some local resources connected to the internet via an ordinary ISP with dynamic IP allocation. To be more specific, these resources are distributed over several locations and so I have several dynamic IPs to manage. Until now, I took the easy way using DynDNS.org. Unfortunately they changed the policy for the free service once again demanding manual login on their website every 30 days, which is a real pain in my situation. Of course I can simply migrate to another service, but on my opinion this is not a clean solution.

First of all I don't want to send my IP address to any company anymore. You all read the news about the PRISM affair and I don't think, it makes any sense to fight against data preservation here in Europe and willingly distributing the IP addresses to the NSA... But on the other hand there is a technical issue, too. Using these services requires setting up an account for each location and so it is not possible to manage all of my resources with one DNS address. Furthermore, I would strongly prefer to union these resources under one of my own domain names, running my websites. This would be a far more clean solution than hopping from one of this free domain forwarders and use one of the silly domains they provide.

So how can I manage this? Is there a tutorial implementing my scenario? I found only the other way round.

Thanks for your advice.

garbage

---

### Post by Lars Noodén on 2013-06-12
You can easily make a HTTP or HTTPS based lookup service that returns the external IP address of the client.  The address can be found under the environment variable *REMOTE_ADDR*  Put the script behind a username and password if you don't want to provide a public service.  You could use perl or even a shell script.

```

#!/bin/sh

echo -n "Content-type: text/plain\n\n";
echo ${REMOTE_ADDR};

```

Then all you need on the client is a script to make a HTTP GET request to the right URL, passing along a user name and password if you've set it that way.

---

### Post by sanderj on 2013-06-12
@garbage98

AFAIK, you would need:

1) a (sub)domain you own / manage
2) a nameserver for that (sub)domain
3) some kind of authentication / authorisation (username/password checking)
4) a mechanism to put the incoming dyndns-request into your (sub)domain zone on your nameserver

So ... as a start: do you have 1 and 2?

---

### Post by garbage98 on 2013-06-12
@ all: Thanks for your support.

@ sanderj:
I have four domains for my web pages directed to my server-IP. I don't have any nameserver running on the machine I am aware of. In principle, managing subdomains should be possible as the domain is linked to my server. Redirecting subdomains is not implemented yet. I only have a config for my apache server redirecting the domains, but I don't think this is enough.

The plan is to use the built-in DynDNS support of my routers, to connect to my server. So I think we have to implement point 2-4 on your list.

@Lars:
Thanks for your advice. As mentioned above, I would like to use the built-in DynDNS support as I have a heterogeneous network behind the router with no reliable device to instantiate the request besides the router itself.

---

### Post by sanderj on 2013-06-12
Do you only want one host / FQDN?

---

### Post by garbage98 on 2013-06-12
I have two routers with dynamic IP.

---

### Post by lisati on 2013-06-16
BUMP
<aside>
I'm [s]grumpy[/s] dissatisfied with DYNDNS too, after they cancelled my free hosts without warning a couple of days ago. No sign of any warning email. What's even more annoying is that one of the domains seems to have been set to someone else's page..... I'm waiting to hear back from them.
</aside>

---


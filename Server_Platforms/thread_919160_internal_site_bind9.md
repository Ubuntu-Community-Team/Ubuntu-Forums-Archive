---
title: "internal site bind9"
date: 2008-09-13
forum: Server Platforms
---

### Post by kebab on 2008-09-13
Hello. 

I'm learning to set up a webserver. To do this I have followed this guide ([http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)) for configuring the server and then this ([http://www.isp-control.net/documentation/start/installation/ubuntu](http://www.isp-control.net/documentation/start/installation/ubuntu)) other to install a control panel hosting.

Once the configuration I put a couple of sites outside the test and my network everything works: the sites are and I can use the control panel user-level.
If, however, enter the site from a PC inside the network this is not seen.

I have sailed much on google and various guides and I came to the conclusion that bind9 is my problem.
Unfortunately I am not a technician and I can not understand how to properly configure bind9 to see sites in internal LAN.

Someone I could kindly help solve the problem? About two weeks that I'm working but without result.

Thank you all!

P.S: sorry for my English!

---

### Post by cattox on 2009-04-06
Hi,

You kind a run into my problem. I was trying to configure bind9 to serve my public url to my local server ip...

... so far with no success.

If you get things to work, please let me know.

Can anyone give us a hand on this?

---

### Post by schettj on 2009-04-06
Seems to be coming up a lot lately... the problem is in your router or firewall, it doesn't do NAT Loopback correctly.

---

### Post by netztier on 2009-04-06
> **cattox said:**
> 
You kind a run into my problem. I was trying to configure bind9 to serve my public url to my local server ip...


BIND doesn't serve URLs, BIND serves DNS queries.

If we assume a generalized URL to be

```
protocol://host.domain.tld:port/path/to/ressource
```

then DNS (and it's most common implementation "BIND") can only help with the **host.domain.tld** part, not with the port, not with the /path/to/ressource. BIND just doesn't have a clue about it.

Among the different possible scenarios to solve your problem, you can find this one:

[LIST]

[*] Run two instances of DNS: a "public DNS" and a "local DNS"
[COLOR="DarkGreen"][*] one instance is hosted on the Internet with a DNS provider of your choice, probably configured via their web GUI or "control panel".
[*] all names in the domain on the public DNS point to internet-reachable addresses or internet-resolvable aliases (aka CNAMEs), and "everyone else" on the internet should use that/these servers to resolve names in your public domain.[/COLOR][COLOR="Navy"][*] one instance is hosted on your LAN and is authoritative for the *same* domain.
[*] Some names your domain on the local DNS can point to local IP addresses or be CNAMEs to your internal domain, some can point to public addresses or internet-resolvable CNAMEs.
[*] this local DNS does not answer any queries from the internet. Check the **allow-recursion {}** option.
[*] this local DNS resolves other domain names via the internet. Check for the **forwarders{}** option[/COLOR]
[/LIST]

Downside: some entries must be done in two different places: [COLOR="DarkGreen"]once on the public DNS with records that reflect the "internet perspective"[/COLOR], [COLOR="Navy"]once on the local DNS to reflect the "local perspective"[/COLOR]. The local DNS will never query your public DNS for anything - because it considers itself as "knowing it all" (read: "authoritative") about your domain. So as the DNS admin, you have to make sure that the local DNS' zonefile contains *all* the required records of your domain - and this in a way that they are correct for a local LAN client.

Upside: you don't need to allow incoming DNS queries to your home hosted (?) server - which you don't want eating away at your bandwith anyway, would you? And you can have the "local DNS" be a lot more specific about your internal hosts - information that doesn't need to be available on the public DNS anyway.

There are variants of this scenario, even with hosting both public DNS and local DNS on the same machine and giving out different DNS replies based on the querier's source IP address (read up about "views" on BIND). Essentially, it's the same, but more complex...

regards

Marc

---


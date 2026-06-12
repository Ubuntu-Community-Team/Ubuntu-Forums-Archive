---
title: "Bind9 mangles my name servers on reboot"
date: 2010-11-26
forum: Server Platforms
---

### Post by annoyingrob on 2010-11-26
I've been having this problem forever, and it's really confusing me. I'm running 10.04, but I believe I had this problem on 9.10 too.

Basically, I have a domain set up on my internal network, and it all works perfectly. The name server for the forward and reverse domains point to "192.168.4.2", which is itself. When I reboot the machine, the name server entries in both the forward and reverse zones are somehow changed to "192.168.4.2.". Notice the extra period at the end of the IP address. This breaks the server, and I have to go in and manually change the entries every time I reboot. Does not happen when simply shutting down and starting bind, only when the machine is rebooted.

Does anybody have any idea why it's doing this?

---

### Post by Vegan on 2010-11-26
Do you have any other programs that are interacting with BIND?

Read the manual closely on their web site. BIND is very complex and it took me weeks to figure it out properly.

---

### Post by bab1 on 2010-11-26
> **annoyingrob said:**
> I've been having this problem forever, and it's really confusing me. I'm running 10.04, but I believe I had this problem on 9.10 too.

Basically, I have a domain set up on my internal network, and it all works perfectly. The name server for the forward and reverse domains point to "192.168.4.2", which is itself. When I reboot the machine, the name server entries in both the forward and reverse zones are somehow changed to "192.168.4.2.". Notice the extra period at the end of the IP address. This breaks the server, and I have to go in and manually change the entries every time I reboot. Does not happen when simply shutting down and starting bind, only when the machine is rebooted.

Does anybody have any idea why it's doing this?

It sounds like there is some misconfiguration either in BIND or an application that interacts with BIND.  I would up the debug level and check the logs.  What entities are allowed to modify the file?  The trailing dot is correct for a DNS FQDN.  As described [**_here_**]("http://en.wikipedia.org/wiki/Fully_qualified_domain_name"): *"In the Domain Name System, and most notably, in DNS zone files, a fully qualified domain name is specified with a trailing dot." *

---

### Post by annoyingrob on 2010-11-30
I know that DHCP updates my DNS records, but I don't know if it would have the ability to modify the name server. My understanding is that with the period at the end, bind treats the ip as a hostname.

---

### Post by bab1 on 2010-11-30
> **annoyingrob said:**
> I know that DHCP updates my DNS records, but I don't know if it would have the ability to modify the name server. My understanding is that with the period at the end, bind treats the ip as a hostname.

Nope.  Using a trailing dot (.) is the proper way to state a FQDN.  See [**_here _**]("http://serverfault.com/questions/108860/domain-tld-vs-domain-tld").

---

### Post by kevinthecomputerguy on 2010-12-01
I wonder if using "localhost" instead of "192.168.4.2" would work.
 
Because localhost. should still be a usuable name.
 
I would be careful, I have a local dns server working without these problems, so even if this works you may still want to look deeper into it.
 
-Kev

---


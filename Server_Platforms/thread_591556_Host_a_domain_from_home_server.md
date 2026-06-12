---
title: "Host a domain from home server"
date: 2007-10-25
forum: Server Platforms
---

### Post by godsfshrmn on 2007-10-25
Do I need to get an external DNS host to do this? I have a static IP through my ISP. I tried to get BIND setup to get a nameserver on my home server but I could never get it to work.

---

### Post by MJN on 2007-10-25
No, you can provide the DNS yourself - particularly as your IP won't change.

The key (aside from configuring the sever correctly of course!) is that your parent zone (e.g. .com in the case of yourdomain.com) needs to delegate the authority for your domain (which I am assuming you have already purchased) to your machine(s). Then, when clients query your name(s) and traverse the DNS they are directed to your nameserver to resolve your records.

Note also a common gotcha - you will need to get a 'glue' record entered into the parent zone also if the name of your nameserver is within your own domain (e.g. ns.yourdomain.com).

Have a read of [http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system) which appears to give a nice overview of how DNS works without getting lost in the techy details of BIND configuration (which will be the next step!).

All said and done you may wish to use a 3rd party DNS provider (plenty of free ones available, e.g. [www.zoneedit.com](www.zoneedit.com) is who I use as I'm on a dynamic IP) as they can let you get familiarity with DNS configuration at a higher level without getting knee deep in the dirt. It all depends on what you want to achieve - if you just want your names resolving let someone else do it, if you want to learn the ins and outs of DNS for its own sake then get reading!

Mathew

---

### Post by godsfshrmn on 2007-10-25
Do you know of any tutorials on how to set this up? I used one for BIND here and no luck. I assume the two need to sync up? Can multiple name servers (i.e ns1.domain1.com and ns1.domain2.com) use the same IP address?

---

### Post by MJN on 2007-10-26
I don't know of any tutorial off-hand, but I'm sure someone can recommend one (or search around).
 
I'm not sure what you mean by your last question - I don't think you're asking what you intended. Can you elaborate? (if it's any help you can only have one name server per IP address (as you can only have one service listening on a port) but it can be serving multiple zones/domains)
 
Mathew

---

### Post by BrentNewland on 2007-10-26
All of the guides are WAY too complicated - setting up bind? Your own DNS? Glue?

Easiest way I've found is everydns.net. Just point your domain to their DNS servers and install their client on your computer. Whenever your IP changes it'll update the everydns.net IP associated with your account. Not recommended if you have an IP that changes daily.

Once that's done, add a record for your domain to your server, and you're all set.




(BTW, EveryDNS is operated by OpenDNS)

---

### Post by aznboy on 2007-10-27
Get a Control Panel....webmin, vhcs, those to come to mind as I believe they support debain so should work for ubuntu...

They both have manuals on how to set everything up I believe..

Then make sure on your domain provider that you have dns setup to point to your IP...

If you can install a os, you can do this for sure

You can also visit this link:

[http://www.howtoforge.com/perfect_server_ubuntu7.10]("http://www.howtoforge.com/perfect_server_ubuntu7.10")

Show you how to setup ubuntu for ispconfig hosting control ...

[http://www.ispconfig.org/manual_installation.htm]("http://www.ispconfig.org/manual_installation.htm")

---


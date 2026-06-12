---
title: "Bind?"
date: 2011-05-24
forum: Server Platforms
---

### Post by us11csalyer on 2011-05-24
Can I run BIND on Ubuntu 11.4 (non-server install)?

If so will I be able to create my own domains with this for free? (Not paying a company to host my domain name)

---

### Post by SeijiSensei on 2011-05-24
> **us11csalyer said:**
> Can I run BIND on Ubuntu 11.4 (non-server install)?

Yes.

> If so will I be able to create my own domains with this for free? (Not paying a company to host my domain name)

You wouldn't have to pay for hosting your domain records, but you'll still have a pay a registrar for the domain itself.  You can't just create domains on your own unless you're not intending to publish them on the public Internet.

On the registrar's site you should be able to point to your own server as the primary DNS.  You'll still need to have a secondary DNS server; maybe the registrar can handle this.  Of course, your DNS server will have to be publicly visible and have a working fully-qualified domain name with an A record.

Unless you really know what you're doing, I'd recommend using the registrar's DNS servers.

---

### Post by HermanAB on 2011-05-25
Use the Domain registrar's servers.  You will be paying for them anyway...

---

### Post by brettg on 2011-05-25
As others have said, you first have to register a domain name (if you want the domain to be reachable from the public Internet)

This costs a about $20 every couple of years, depending on who you use as your registrar. The other cost comes in hosting the name records, which is where bind steps in.

The answer is yes, you can use bind to host a domain. If you want it to be publicly available you will need to register it first. You may find that your registrar gives you free domain hosting along with your registration.

If you want to;

a) host a publicly accessible domain yourself anyway

or 

b) create a private domain for your office or home network to use that cannot be resolved from the public Internet

then you can indeed do both these things with bind.

See [this guide]("http://tuxnetworks.blogspot.com/2011/01/howto-caching-authorative-nameserver.html") for details on configuring bind

---


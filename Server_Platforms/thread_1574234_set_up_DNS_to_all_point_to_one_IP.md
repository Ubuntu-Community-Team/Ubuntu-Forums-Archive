---
title: "set up DNS to all point to one IP?"
date: 2010-09-14
forum: Server Platforms
---

### Post by jlhw on 2010-09-14
hey all - 
how would i go about setting up a server running 10.04 to resolve all incoming DNS requests to one IP address? these DNS requests will be coming through the internet on port 53 from a router i installed on the remote subnetwork. Any help is much appreciated!! :)

---

### Post by CharlesA on 2010-09-14
You mean like forward all DNS requests to one server?

You might be able to use iptables, but I don't know.

---

### Post by terazen on 2010-09-14
You can use an asterisk in a bind record, but I'm not sure if that's what you need.  What exactly are you trying to accomplish?

---

### Post by jlhw on 2010-09-14
I work for a solar power monitoring company. We just took over an account from a different company, so now we need to get the data from a competitor's equipment to start sending to our data acquisition servers. I shipped them a router that had been configured to send all DNS requests to our IP address. Now I need to have a server on this end that will take all those DNS requests and resolve them to our data acquisition servers, regardless of their original destination.

Thanks so much for your help!!

---

### Post by endotherm on 2010-09-14
> **jlhw said:**
> I work for a solar power monitoring company. We just took over an account from a different company, so now we need to get the data from a competitor's equipment to start sending to our data acquisition servers. I shipped them a router that had been configured to send all DNS requests to our IP address. Now I need to have a server on this end that will take all those DNS requests and resolve them to our data acquisition servers, regardless of their original destination.

Thanks so much for your help!!
I would set up forwarders on your extranet dns server (the one everyone is already pointed to), pointing to your internal dns.

---

### Post by terazen on 2010-09-14
If you knew what names the equipment was trying to resolve that would be easy, but I guess you don't know those?

The only way I can think of is like this on a bind server:
```
*.something.com.          IN      CNAME   something.else.com.
```
or
```
*.something          IN      CNAME   something.else.com.
```
I'ver never tried it as just "*", but maybe it will work I'm not sure.

---

### Post by koenn on 2010-09-14
+1 for terazen.

No matter how you route, redirect and forward those DNS requests, at some point, a DNS server is going to have to take the name and return the matching address. 
However, it will only do so if it has a valid A or CNAME record, either in a zone file or in cache, but caches expire sooner or later. 
So your DNS server  needs authority over the domain name in order to resolve the FQDNs (even if you can wildcard the host name portion of it).

---

### Post by jlhw on 2010-09-14
wow, thanks very much everybody. i made the changes suggested by terazen, and now i'm looking into transferring authority to my DNS server. i think i should be good from here.

thanks again, all, and message me if you're ever in Portland, OR and I'll buy you a beer or coffee!

---


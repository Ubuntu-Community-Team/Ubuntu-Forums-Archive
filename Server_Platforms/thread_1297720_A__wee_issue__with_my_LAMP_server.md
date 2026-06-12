---
title: "A  wee issue  with my LAMP server"
date: 2009-10-22
forum: Server Platforms
---

### Post by immerohnegott on 2009-10-22
Ok, so I've been running a small-time site from a near decade-old laptop in my closet (professional I know, but thanks to the wonders of Ubuntu, the old girl is doing pretty well). This is in a virtual server on my router (basically hyped up port-forwarding), using a DDNS service to keep the domain up.

With the pleasantries out of the way, here be the problems.

Upon checking the apache access.log, I discovered a veritable boatload of requests from a number of IPs doing GETs and POSTs on external sites. From what I googled, this is an attempt to use my server as a proxy. The connections are getting 404s as far as I can tell, but this is still a lot of inbound traffic that I don't want to deal with.

Is there anything I can do to block these entirely? I guess I can't keep them out entirely since port 80s wide open....but, any thoughts?

---

### Post by dominiquec on 2009-10-22
Blacklist those IP addresses?

---

### Post by Lars Noodén on 2009-10-22
You can use tcpd to blacklist those sites.  See [hosts.allow](http://linux.die.net/man/5/hosts.allow)
[hosts.deny](http://linux.die.net/man/5/hosts.deny)

You can also use iptables to blacklist those sites or in general to limit the rate at which your web server gets hammered. 
 
Here is a rather clever example of tiered limits, where misbehaving addresses get banned for longer and longer.  It uses ssh, but with only a little modification, it will work fine for http and https, too:
[http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/](http://www.e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

---

### Post by immerohnegott on 2009-10-28
Thanks. 

I'll dilly about with iptables when I get some time (school for the lose). From looking through the logs, most of these requests seem to be coming from the same half-dozen or so IPs, so blacklisting them would work. I guess this is what I get for trying to learn all of this on my own.

---

### Post by Lars Noodén on 2009-10-28
> **immerohnegott said:**
> most of these requests seem to be coming from the same half-dozen or so IPs, so blacklisting them would work. I guess this is what I get for trying to learn all of this on my own.

When you do block them, you can send off a message to the ISP and let them know why.

You can find the ISP contact name using the ip number of the offinding machine and the program [whois](http://manpages.ubuntu.com/manpages/karmic/en/man1/whois.1.html).

Whois can also tell you the range of addresses, so it might be possible to add a block rather than just one at a time.

---


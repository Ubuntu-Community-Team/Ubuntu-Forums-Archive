---
title: "Changing DNS Domain Name in Ubuntu"
date: 2010-06-29
forum: Server Platforms
---

### Post by Thyagaraj on 2010-06-29
what is the best way of changing DNS Domain name in ubuntu 8.10?
My server has bind installed and I can configure dns by webmin.
I've all the configuration files under /etc/bind/.
eg:[www.abc.net](www.abc.net) to [www.xyz.com](www.xyz.com)

---

### Post by Thyagaraj on 2010-07-22
please any one help me...

---

### Post by denver on 2010-07-22
Well, this might be an extensive response, but its all based on what you really want to achieve.

If for example you want to associate a hostname to an IP address present on your system, and you want the whole world to know it, you will first need to own, or purchase a domain name. You will then need to have 1 or more (more is better) nameservers set for the domain name (you usually do this at the registrar you got the domain from) and in those nameservers, you need to have the proper DNS entries. You may use your own PC as a nameserver, but if that PC goes down, your domain name will not resolve. 

That way, when someone wants to access [www.xyz.com](www.xyz.com), they will ask the Top Level Domain for .com, which nameservers are set for xyz.com. From there, the user is directed to the nameservers you set for the domain. Those DNS servers will then be asked what IP or hostname is associated to a particular entry (MX, A record, NS, CNAME, etc).

IF however you want to be accessible only in your Local Area Network via a domain name, you don't necessarily need to register a domain OR do any of the steps above. Most LAN's have a caching nameserver (eg: dnsmasquarade) which accepts custom DNS entries and will respond with whatever IP you tell it [www.xyz.com](www.xyz.com) should have.

IF you only want to change your hostname and don't really care if the rest of the world knows it, you only have to edit:

```

/etc/hostname

```

and run the following command:

```

hostname -F /etc/hostname

```

Depending on which of these best describes your situation, it may or may not be enough to make a few settings on your local machine. You may need to register a domain or employ a geographical redundant DNS system, if you care about your uptime.

Good luck!

---

### Post by Iowan on 2010-07-22
It's not a bad idea to edit */etc/hosts* and */etc/hostname* at the same time - otherwise **sudo** complains.

---

### Post by Thyagaraj on 2010-07-25
I could able to change entire domain name. But the problem is I've ldap installed on it with ldap users and groups.

---


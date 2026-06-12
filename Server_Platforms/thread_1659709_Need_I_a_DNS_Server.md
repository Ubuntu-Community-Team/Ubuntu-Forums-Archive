---
title: "Need I a DNS Server?"
date: 2011-01-04
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-01-04
Hi everyone,

I am trying to install a ubuntu server to serve sites. More than one, so I´ll use Apache VirtualHost.

When installing ubuntu server ask me about installing DNS Server? do i need it? :confused:

Thanks in advance!

---

### Post by aceofspades686 on 2011-01-04
It depends on exactly what you're doing.  If this is just going to be for an internal network with a few computers, I would say no because its easier just to add your websites to the host file.  If its for an internal network with a lot of computers then it would be worth it so you don't have to edit all the host files.  If its going to be accessed over the internet, you'll need to register your domain with a domain provider so the root DNS servers can point to your IP.

---

### Post by aceofspades686 on 2011-01-04
-Deleted, not sure why it doubleposted what I said-

---

### Post by acastrolorenzo on 2011-01-04
Its for Internet. Root DNS server?, sorry I had no clear idea about DNS.

---

### Post by aceofspades686 on 2011-01-04
You'll need to register your domain with a domain name provider so that the URL you want can point to your IP address.

DNS is simply that, a server that resolves a URL to an IP address.  If you register with an external provider to get your domain on the internet's root DNS, then you won't need an internal DNS.

---

### Post by HermanAB on 2011-01-04
Howdy,

It is much less of a pain to simply use the DNS service provided by the company where you register your domain names.  You pay them, so you can just as well use them.

---

### Post by acastrolorenzo on 2011-01-04
Thanks!

Thats what I thougt, but wasnt sure when saw the option "DNS Server" when installing Ubuntu Server. :p

---


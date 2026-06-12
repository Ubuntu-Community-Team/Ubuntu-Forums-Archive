---
title: "DNS Bind ddclient or router"
date: 2009-08-03
forum: Server Platforms
---

### Post by dannyr on 2009-08-03
Hi
I am completely new to Ubuntu.  I have installed v 9.04 server version.  My question is what is the best way to manage DNS.  I have a Dynamic IP and my server is connected via a router.
I am able to alter DNS settings in the router.  after reading a lot of other threads I am confused as to the best way to handle the DNS side.  The server will only host up to 3 domains ( one at the moment).
Is my best option to use OpenDNS and just set the router, use BIND or DDclient to sort out the DNS.  My main concern is the propogation for the IP change through the WWW and if openDNS is suitable for quick propogation through UK DNS servers or perhaps one of the other methods ?
Still a bit confused can anyone help.?

---

### Post by cdenley on 2009-08-03
Are you trying to configure DNS so users on your network can resolve DNS names like [www.google.com](www.google.com), or are you trying to configure a server so other people can access it using a domain you purchased such as [www.mydomain.com](www.mydomain.com)?

---

### Post by dannyr on 2009-08-03
> **cdenley said:**
> Are you trying to configure DNS so users on your network can resolve DNS names like [www.google.com]("http://www.google.com"), or are you trying to configure a server so other people can access it using a domain you purchased such as [www.mydomain.com]("http://www.mydomain.com")?

Hi
I would like to configure the server for a purchased domain, so that people can access it.  [www.mydomain.com](www.mydomain.com).

---

### Post by cdenley on 2009-08-03
> **dannyr said:**
> Hi
I would like to configure the server for a purchased domain, so that people can access it.  [www.mydomain.com](www.mydomain.com).

Where did you purchase it from. Usually, whoever you purchased it from will provide DNS services as well. Since it sounds like you are using a simple DNS configuration, I would suggest you do that.

---

### Post by dannyr on 2009-08-03
> **cdenley said:**
> Where did you purchase it from. Usually, whoever you purchased it from will provide DNS services as well. Since it sounds like you are using a simple DNS configuration, I would suggest you do that.
Hi, I purchased from [www.123-reg.co.uk](www.123-reg.co.uk)  They do handle DNS but it seems that a fixed IP is required.  There does not seem to be an option for 'auto' update of the dynamic IP !

---

### Post by cdenley on 2009-08-03
> **dannyr said:**
> Hi, I purchased from [www.123-reg.co.uk](www.123-reg.co.uk)  They do handle DNS but it seems that a fixed IP is required.  There does not seem to be an option for 'auto' update of the dynamic IP !

Generally, a static address is required for DNS, unless you set a really short TTL and had an external DNS server which is constantly updated by your server. I know [www.dyndns.com](www.dyndns.com) can do this with a free domain. I would assume you could transfer your purchased domain to them. You couldn't run your own DNS (bind) with a dynamic IP.

[http://packages.ubuntu.com/hardy/ddclient](http://packages.ubuntu.com/hardy/ddclient)

---


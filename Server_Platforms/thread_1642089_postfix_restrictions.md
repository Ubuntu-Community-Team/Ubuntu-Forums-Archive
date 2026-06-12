---
title: "postfix restrictions"
date: 2010-12-09
forum: Server Platforms
---

### Post by Underpants on 2010-12-09
I'm working on setting up some postfix servers on my network.

Their function is simple I believe. 

I have 2 internal domains (domain1.com and domain2.com) that are identified in my transport file and look something like this: 

```

#/etc/postfix/transport
domain1.com     smtp:[exchFE.fqdn.lan]:25
domain2.com     smtp:[exchFE.fqdn.lan]:25

```

Any mail that is not addressed to one of those domain names, should be delivered to the relayhost as defined in the main.cf file.

```

#/etc/postfix/main.cf
relayhost = 172.16.x.x
~~~ SNIP ~~~

```


I need to put some restrictions in place. 

I need to be able to define a list of IP addresses that can send to the 2 internal domains, and a seperate list of IP addresses that can use the relayhost. 

How would you go about this? 


 - The background: This is a large multi subnet LAN. We have dozens of servers on our production network that need to send emails to various employees (on an Exchange server) with logs from jobs, information, whatever.

Some of the scripts and jobs need to email vendors and external domains. The relay host is in a DMZ and it is another SMTP server that our webservers use to relay mail. That smtp server relays to an external third party who scrubs scans and sends.

---


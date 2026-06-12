---
title: "Dns"
date: 2007-08-02
forum: Server Platforms
---

### Post by Tabenx on 2007-08-02
My websites working and all but i was wondering how i can actually get nameservers so it can work with my domain.

---

### Post by ev5unleash1 on 2007-08-02
I have a website too but i'm not to into that stuff of DNS it can sometimes get on your nerves. Just link the IP address of your site or just use parked servers that most domains come with.

---

### Post by murraymca on 2007-08-05
Are you talking about running a website privately on your own domain that doesn't get accessed from anyone over the internet?

If so you can just edit /etc/hosts and put in say:

127.0.0.1 your.fully.qualified.domain www

So then when you browse to either www/your FQDN you will (should) be directed to your website (if you are on another machine just replace the localhost IP address with that of your server)

---


---
title: "Adding domain names"
date: 2012-10-12
forum: Server Platforms
---

### Post by DonTommy on 2012-10-12
Hey
I got an apache webserver set up on ubuntu, I got a domain which is pointed to it IP, I got the domain to resolve but only on localhost.domain.com
How can I configure it, so that domain.com also will work?

Thanks

---

### Post by volkswagner on 2012-10-12
I think you may have to provide more detail.

Two things come to mind.
[LIST=1]
[*]You need to properly setup namebased virtual hosts.  You can check the Apache server docs sticky for help [here]("https://help.ubuntu.com/10.04/serverguide/httpd.html").
[*]You may be experiencing  a NAT issue.  Perhaps your router is not allowing you to access the domain internally.  Can you  access the domain from a machine outside of  your LAN.
[/LIST]

---

### Post by DonTommy on 2012-10-12
Hey
Yes I am able to access the index.html from localhost.domain.com from the internet, outside my lan

I already tryed playing around with that guide, and setting it up like that with virtual hosts, but no change, still only localhost.domain.com that works. If I type the IP directly in my browser I get the page, if I type localhost.domain.com I get the page, but domain.com just get me a  page not found/cannot display this webpage

---

### Post by volkswagner on 2012-10-12
I don't understand.  Do you have a dns entry for localhost.domain.com?  Or do you have a wildcard dns entry.  I'm just not sure why localhost.domain.com would even resolve externally.

Please post your vhost file and what dns entries you have.

What is the output of the following?

```
host domain.com
```
```
host localhost.domain.com
```
```
dig domain.com
```

---

### Post by DonTommy on 2012-10-12
Ahh think you pointed me in the right direction, the localhost.domain.com resolves because the place that handles the dns got that as host, so just added domain.com as well, so it might work when the dns updates...

Thanks for your time ;)

EDIT: It worked when I set up right at the dns provider adding the domain.com along with localhost.domain.com which cant be removed ;)

---

### Post by volkswagner on 2012-10-12
Glad you got it working.

Please mark thread as solved using the "thread tools" link.

---


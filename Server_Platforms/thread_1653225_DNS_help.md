---
title: "DNS help"
date: 2010-12-26
forum: Server Platforms
---

### Post by Monotoko on 2010-12-26
I was wondering how to set up nameservers so that I can start lending out server space to friends and colleuges. I have a dedicated server with two IP addresses, I'm not quite sure how to set up nameservers so that people can buy their domains, point them to my nameservers and then the server should be able to deal with it from there (I can manage that bit)

Can anyone help explain how to set up two nameservers that point to my dedicated server?

---

### Post by minigilani on 2010-12-26
dyndns.com and no-ip.com provide services that route a sub-domain name to an ip. Like, if i were to set up "minigilani.kicks-butt.net" to point to my ip address, anyone connecting to that address will connect to my computer.

---

### Post by robert_pectol on 2010-12-26
First, make sure your server IP address is a static, publicly routable IP and if you can have your provider assign a meaningful reverse delegation for it, all the better. Then, install Bind 9 and configure applicable zones for the domains you will be hosting.  You'll want to configure a slave or two at some other location(s) to slave your zones for robustness.  Then instruct your users to have their registrars point their domains to your server and slave(s).

---


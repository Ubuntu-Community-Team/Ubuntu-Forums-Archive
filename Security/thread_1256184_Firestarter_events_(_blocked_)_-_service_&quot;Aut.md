---
title: "Firestarter events ( blocked ) - service &quot;Auth&quot; .. what it means ?"
date: 2009-09-02
forum: Security
---

### Post by credobyte on 2009-09-02
Does it really mean that someone is trying to login into my machine ? If not, what exactly it means and is there a place where I could find more information about these events/services ?

---

### Post by XCan on 2009-09-02
[http://www.grc.com/port_113.htm](http://www.grc.com/port_113.htm)

---

### Post by credobyte on 2009-09-02
> **XCan said:**
> [http://www.grc.com/port_113.htm](http://www.grc.com/port_113.htm)

Thank you!

---

### Post by cariboo on 2009-09-02
What you are seeing is perfectly normal, welcome to the internet.

What you are seeing is more than likely a bot looking for holes in your firewall.

---

### Post by credobyte on 2009-09-02
> **cariboo907 said:**
> What you are seeing is perfectly normal, **welcome to the internet.**

What you are seeing is more than likely a bot looking for holes in your firewall.

Heh, well .. most probably you are right - I've finally ( 4 years without an anti-virus or firewall .. obviously, no interest @ what services are there and why do we need them ) started to learn more about networking and firewalls - that's why I run into quite many questions lately :)

---

### Post by cdenley on 2009-09-02
All that tells you is there was a blocked packet coming from that IP on that TCP or UDP port. The service name given is just the most common service which utilizes that port. It was probably blocked because it was not related to any connections which were established by you. Unless you installed server software which listens on those ports, those connection attempts would be rejected even if they weren't filtered by the firewall. If you want to know more actual information about any traffic, you will need to capture it with wireshark, or a similar program, while you receive it.

There are many reasons for these unsolicited packets. It could be a script or attacker looking for unsecured servers. If you have been using P2P (bittorrent) recently, others peers may be trying to download from you. If you recently received a new IP address from your ISP, they may be trying to connect to a person who previously used that IP.

I don't recommend using firestarter. It is old, and no longer maintained.

---


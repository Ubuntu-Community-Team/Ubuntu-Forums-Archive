---
title: "My ISP blocks incoming port 25 connections what can i do?"
date: 2008-09-01
forum: Server Platforms
---

### Post by crhossen on 2008-09-01
I'm trying to setup a mail server in my dorm room. I am able to send messages to people but I cannot get any messages to get back to me. When I try to telnet into port 25 from outside my network it cant connect. I tried changing smtp to listen at 587... same thing. Do you guys have any other ideas?

---

### Post by TreeFinger on 2008-09-01
ask ISP to allow incoming connections on port 25 is all I can think of.

---

### Post by unsoc on 2008-09-01
I have problems at times sending mail from my server using my email client. I have to use my ISP's smtp settings to send.

If you have a email account with your school try using their pop3

---

### Post by crhossen on 2008-09-01
Well I don't think asking them to open the port for me would get anywhere. They just switched the resnet to using dynamic ips. So their network is a little funky right now. Last year we had static ones. I can get messages out fine. Using my school's pop isn't as fun. I want to be able to use my own domain for my mail address. Also I had some projects in mind that would need mail receiving to work.

---

### Post by schettj on 2008-09-02
Upgrade to a static IP level of service. That's why they cost more...

---

### Post by b20963a2 on 2008-09-02
You could use a service like DynDNS to forward e-mail to an alternate port: [http://www.dyndns.com/services/mailhop/relay.html](http://www.dyndns.com/services/mailhop/relay.html)

I would need to do the same thing with my provider (all incoming ports under 8000 are closed.)

---

### Post by crhossen on 2008-09-02
> **schettj said:**
> Upgrade to a static IP level of service. That's why they cost more...

We used to get Static IPs last year. But now they are running out of IPs at my school (RIT) so they switched the Resnet to dynamic. The dyndns mailhop is kinda pricey. I'm trying to find a free way to do it.

---

### Post by windependence on 2008-09-02
As was mentioned you could switch to a commercial account (they aren't that much more).

no-ip has a special service for this also. It's called relector.

[http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html](http://www.no-ip.com/services/managed_mail/inbound_port_25_unblock.html)

-Tim

---


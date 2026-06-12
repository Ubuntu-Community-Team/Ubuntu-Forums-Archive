---
title: "Can't receive mail on Dovecot/Postfix server"
date: 2011-03-10
forum: Server Platforms
---

### Post by Kozley on 2011-03-10
I do not know why I could send e-mail outside but not receive. I use relay to my ISP that port 25 is blocked by my ISP. What can I doing with configuration when it should be works to receive mail?

Okay, I have sent a test e-mail between localhost and it works. I can send from mailserver to my gmail without problem. So why I cannot receive e-mail from gmail?

---

### Post by SeijiSensei on 2011-03-11
Most likely reasons:

Your server is configured to listen only on localhost (127.0.0.1) and isn't listening on the machine's network address (check the smtp_bind_address parameter in Postfix). Or it's configured to only accept mail from a small range of addresses (the "my_networks" parameter in Postfix).

Your firewall isn't configured to pass port 25 traffic through to the server.

Your ISP blocks inbound port 25 connections.  Running a mail server on a residential connection is usually a violation of the ISP's terms-of-service.  Some ISPs block inbound ports 25 and 80 as a result.

---

### Post by Kozley on 2011-03-13
> **SeijiSensei said:**
> Most likely reasons:

Your server is configured to listen only on localhost (127.0.0.1) and isn't listening on the machine's network address (check the smtp_bind_address parameter in Postfix). Or it's configured to only accept mail from a small range of addresses (the "my_networks" parameter in Postfix).

Your firewall isn't configured to pass port 25 traffic through to the server.

Your ISP blocks inbound port 25 connections.  Running a mail server on a residential connection is usually a violation of the ISP's terms-of-service.  Some ISPs block inbound ports 25 and 80 as a result.

Sorry for late reply but I have already solved it with virtual users and database. I was followed howto from HowToForge and it works now.

---


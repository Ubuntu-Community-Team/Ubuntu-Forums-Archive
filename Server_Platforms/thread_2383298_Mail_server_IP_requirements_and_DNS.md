---
title: "Mail server IP requirements and DNS"
date: 2018-01-23
forum: Server Platforms
---

### Post by ascattolini on 2018-01-23
I have a ubuntu-based mail server in my dmz. Mx record is resolved with public ip address a.b.c.d (natted to point to the mail server). When mail server answers, it is shown as public ip address e.f.g.h (in fact it goes out through another gateway). My doubt is: should a.b.c.d=e.f.g.h or is this irrelevant for a mail server? I should avoid my emails marked as spam by other mail servers' spam filters.

Thanks in advance,
Antonio

---

### Post by slickymaster on 2018-01-23
Thread moved to **Server Platforms** for a better fit

---

### Post by SeijiSensei on 2018-01-23
The only address that matters is the public one used during the SMTP exchange.

To protect against your messages not being rejected as spam, that public address needs to have both forward and reverse DNS set up.  There should be an MX record that points to the mail server by name, and an A record for the server's address.  There should also be a reverse entry like 4.3.2.1.in-addr.arpa.  Setting that up will likely require communicating with your ISP.

Another minimal requirement these days is to have an "SPF" record in your DNS.  This is a record of type TXT that designates the valid sending servers for mail from your domain.  See [http://www.openspf.org/Introduction](http://www.openspf.org/Introduction) for details.

---

### Post by ascattolini on 2018-01-25
Ok, thank you very much!

Antonio

---

### Post by TheFu on 2018-01-26
Any SMTP server in a DHCP address range will almost always be marked as spam.  A static IP is required to avoid that, but many VPS subnets are marked as spam too.  When you get a static IP assignment from any provider, check the spam blocklists immediately to see if that IP is lists.

---


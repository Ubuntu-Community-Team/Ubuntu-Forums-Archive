---
title: "MTA for forwarding recommendations"
date: 2007-06-12
forum: Server Platforms
---

### Post by kimmo on 2007-06-12
I need to receive mail on my host but would like to redirect it all directly into my gmail account (including the local crontab mail etc)

I thought nullmailer would be made for me but it's configuration is strange, any tips how I should configure it (*@my.host.dom to [email]my.mailbox@gmail.com[/email]) or suggestions for another package?

---

### Post by Mr. C. on 2007-06-13
With any MTA, you will need first to setup the MX records for your domain.  Then setup your MTA to accept email for the listed recipients in your domain (don't use wildcards, or be prepared for loads of SPAM).  With postfix, setup a virtual alias for your email address(es) that will redirect to your gmail address.  Alternatively, use a transport map.

MrC

---


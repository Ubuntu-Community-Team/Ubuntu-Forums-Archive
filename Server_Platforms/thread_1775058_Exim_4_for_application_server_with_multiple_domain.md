---
title: "Exim 4 for application server with multiple domains"
date: 2011-06-04
forum: Server Platforms
---

### Post by mschipperheyn on 2011-06-04
Hi,

I have an application server with multiple domains/applications. Let's say
domeinx.com - 12.0.0.15
domeiny.nl - 12.0.0.15


I use exim4 and I'm no mail configuration expert. 

The actual smtp server is elsewhere and is identical for both domains. Let's say
mail.mymail.com - 145.1.1.1


The server needs to send application emails. Originally, I just had domainx.com and it seemed to work ok. But now I'm seeing these types of errors on some emails I'm sending

HELO should be a FQDN or address literal


My first question is how to avoid the HELO error

My second questions is how to setup exim to deal with emails that are send with froms such as 
[email]info@domeinx.com[/email]
[email]info@domeiny.nl[/email]

Any help on either of the questions is appreciated

Kind regards,

Marc

---


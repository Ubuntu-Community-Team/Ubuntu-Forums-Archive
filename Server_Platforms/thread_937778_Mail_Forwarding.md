---
title: "Mail Forwarding"
date: 2008-10-04
forum: Server Platforms
---

### Post by bpneiman on 2008-10-04
I want to setup an Ubuntu mail server with it's only task being to forward mail sent to [email]username@inbox.mydomain.com[/email] to [email]username@mydomain.com[/email]

What would be the best way to go about doing this?

If you are wondering "why?", my company uses a 3rd party email hosting provider.  We are unable to receive important email from 3 specific domains for various reasons, and the company we use does not offer the flexibility to allow specific domain through their filters.  I was hoping to get around this by having the users at the blocked domains send email to [email]username@inbox.mydomain.com[/email] and have that mail forwarded to [email]username@mydomain.com[/email]

---

### Post by iponeverything on 2008-10-04
> **bpneiman said:**
> I want to setup an Ubuntu mail server with it's only task being to forward mail sent to [email]username@inbox.mydomain.com[/email] to [email]username@mydomain.com[/email]

What would be the best way to go about doing this?

If you are wondering "why?", my company uses a 3rd party email hosting provider.  We are unable to receive important email from 3 specific domains for various reasons, and the company we use does not offer the flexibility to allow specific domain through their filters.  I was hoping to get around this by having the users at the blocked domains send email to [email]username@inbox.mydomain.com[/email] and have that mail forwarded to [email]username@mydomain.com[/email]


you can set up mail server on machine to receive mail and get whoever is managing DNS for your domain to change the MX entry to point to your box. Then just set up an alias that will forward the incoming mail to the location of your choice.

---


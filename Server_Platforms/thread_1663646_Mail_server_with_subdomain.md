---
title: "Mail server with subdomain?"
date: 2011-01-09
forum: Server Platforms
---

### Post by pspkicks316 on 2011-01-09
I've got a mail server setup (Postfix+Dovecot). I want my mail services (imap, pop3, smtp) to be accessible ONLY via the corresponding subdomain (such as imap.testdomain.com or smtp.testdomain.com).

I have the respective subdomains forwarding to my domain and have port forwarding setup to forward to my server. 

With this setup, however, I can easily substitute smtp.testdomain.com as the imap server, or anything else. 

Is it possible to make the email server services accessible ONLY from the corresponding subdomains?

My DNS records (I use GoDaddy) point imap,smtp,and pop3 subdomains to my domain but in essence they're all the same.

---

### Post by SeijiSensei on 2011-01-10
> **pspkicks316 said:**
> Is it possible to make the email server services accessible ONLY from the corresponding subdomains?

Not unless you have a separate IP address for each service.  Otherwise if all three names point to the same address, there's nothing that the server can do to differentiate among them. Nothing in the primary TCP protocols, other than HTTP/1.1, include a method for the client to pass a specific host name to the server.

---

### Post by pspkicks316 on 2011-01-10
Alright, thank you!

---


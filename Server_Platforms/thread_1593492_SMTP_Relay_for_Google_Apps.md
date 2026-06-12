---
title: "SMTP Relay for Google Apps"
date: 2010-10-11
forum: Server Platforms
---

### Post by josheby on 2010-10-11
The company I work for recently switched to Google Apps for email.  The problem we have now is that our internal systems that send email are no longer able to as our internal mail server is no longer available.

We need to be able to relay mail from multiple domains to users both on Google and other services.  I am worried that if I was to just relay mail for our domains that are being hosted on Google that our domain or IP may get blacklisted since the IP the relayed mail will be coming from is not what reverse DNS will bring up for our MX records which point to Google.

Things to consider:
- Easy Config
- Able to restrict which systems can relay mail via this server.

Thank you to everyone for all help!

---


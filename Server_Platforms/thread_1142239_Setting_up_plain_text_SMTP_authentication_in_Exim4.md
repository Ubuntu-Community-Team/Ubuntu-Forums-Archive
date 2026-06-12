---
title: "Setting up plain text SMTP authentication in Exim4 for LAN and WAN"
date: 2009-04-29
forum: Server Platforms
---

### Post by kevinfishburne on 2009-04-29
I'm configuring an email server using Dovecot and Exim4. It will need to allow several email accounts to send/receive email both within the LAN and from the Internet using unencrypted SMTP authentication.

What's working:
Sending email from internal email addresses to internal email addresses using Evolution/Squirrelmail (webmail)
Sending email from internal email addresses to external email addresses using Squirrelmail

What's not working:
Sending email from internal email addresses to external email addresses using Evolution

I think by default SMTP authentication is disabled in Exim4 and needs to be enabled. I also suspect I need to add usernames and passwords somewhere for SMTP to authenticate against. I'm pretty sure the server's not currently configured as an open relay, but allows relay for localhost only. I'm not using a smarthost and have a static WAN IP address.

Despite numerous guides to set up Exim4 none of them specifically mention the configuration I need (or are outdated or simply do not work). Thanks in advance for any help you can offer to figure this out.

---


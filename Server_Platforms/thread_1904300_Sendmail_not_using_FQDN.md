---
title: "Sendmail not using FQDN"
date: 2012-01-04
forum: Server Platforms
---

### Post by lunchlady55 on 2012-01-04
Hello, 

I have a server with sendmail, and I'm sending messages on a huge corporate LAN.  When I send a message from my server to my personal email, I don't see the FQDN.

Example:

user <user@my-host-name>

This wouldn't be an issue except Outlook is complaining that this may be a phishing attempt and blocks any links that appear in the email. I plan on sending alerts and links to verify the alerts from this server, and this behavior is sub-optimal. 

I have little power to change anything but my own server config. I was hoping that if I could configure sendmail to include the FQDN it might stop Outlook from blocking the URLs and links. 

I have set the FQDN in 
/etc/hostname:
my-host-name.my-domain.com

and /etc/hosts:

127.0.0.1 localhost.localdomain localhost
192.168.0.5 my-host-name.my-domain.com my-host-name

Can anyone help me get sendmail to use the fqdn when sending mail?

---

### Post by smtp on 2012-01-05
Hello,

Best wishes for a Happy New Year.


The configuration file changes needed to implement hostname hiding are:
MASQUERADE_AS(`my-domain.com')
MASQUERADE_DOMAIN(`my-host-name.my-domain.com')
FEATURE(`masquerade_entire_domain')
FEATURE(`masquerade_envelope')

That is.

---

### Post by lunchlady55 on 2012-01-17
Thanks so much, this was exactly what I needed. 

I put this in /etc/mail/sendmail.cf, BEFORE the MAILER() lines, ran sendmailconfig, answered Yes to the questions about using the existing files, and restarted sendmail.  Emails now have the proper domain name.

---


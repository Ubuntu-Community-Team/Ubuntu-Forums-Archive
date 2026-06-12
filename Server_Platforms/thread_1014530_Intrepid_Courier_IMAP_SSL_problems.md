---
title: "Intrepid: Courier IMAP SSL problems"
date: 2008-12-17
forum: Server Platforms
---

### Post by aaron.dunlap on 2008-12-17
Upgraded my server to Intrepid just fine and everything seems to be great except for my Courier IMAP installation.  /var/log/syslog is piling up with the following message (which is coinciding with me trying to retrieve anything from the mail server:

Dec 17 21:51:18 fileserver imapd-ssl: /usr/lib/courier/courier/imaplogin: symbol lookup error: /usr/lib/courier/courier/imaplogin: undefined symbol: auth_sasl_ex

---


---
title: "spamd not receiving mails"
date: 2008-10-23
forum: Server Platforms
---

### Post by Zelos1983 on 2008-10-23
Edit: solved it now, there was a central rule commented out in the exim conf.


Hi there,

I am currently setting up a new mail server with Ubuntu 8.04 64Bit and exim4 (heavy) with spamassassin support. I did enable it in /etc/exim4/sa-exim.conf and made sure it is enable in /etc/default/spamassassin.conf. The process is running and log gets written, but E-Mails are not filtered or modified by spamassassin (as far as I see it should rewrite the subject in the header in default config). There are no log entries in /var/log/spamd.log dealing with mails.

What am I doing wrong? What do I need to do to ensure that the spamd server processes incoming e-mails that are received by exim4, if I start with the default config?

thank you very much for your help!

David

---


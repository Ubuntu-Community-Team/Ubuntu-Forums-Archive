---
title: "Home mail server help"
date: 2007-01-30
forum: Server Platforms
---

### Post by bspratt on 2007-01-30
Can someone please provide some guidance with getting a mail server going. So far I have an Edgy Server on an almost static IP (using no-ip client but only changes like twice a year) running Apache2 (hosting 3 web sites) with Proftpd.  I own my own domain and currently forward [email]emails@mydomain.com[/email] (80% of all my email) to my ISP's (RoadRunner) account and then retrieve. RoadRunner here in Florida does not permit forwarding from them. I would like to have a mail server for the learning experience and to have more control over spam, ads and such. I have been reading about postfix, sendmail, fetch, asassin and other tools and am somewhat confused. Can someone recm'd a good overall solution for serving my email at home? (for getting both domains sent to my server)  Thanks - Bill

---

### Post by MrHorus on 2007-01-31
```
apt-get install exim4 procmail courier-imap courier-imap-ssl
```

Will install a mailserver, a delivery agent and a way for you to access IMAP mailboxes over an encrypted connection and debconf should prompt you for all the information although you will generally only want to be relaying mail for your own domain and localhost.

Before you do this you will need to make sure you have proper DNS setup for your server and that your domain's MX record points to your server otherwise you will have all sorts of problems with mails bouncing and the likes.

---

### Post by bspratt on 2007-01-31
outstanding - thanks for the quick reply - I will try this and report back - Bill

---


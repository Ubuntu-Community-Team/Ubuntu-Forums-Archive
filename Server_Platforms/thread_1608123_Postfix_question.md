---
title: "Postfix question"
date: 2010-10-28
forum: Server Platforms
---

### Post by Solignis on 2010-10-28
Is postfix an open relay by default?

I don't want it to be an open relay and my ability to search google seems to have failed me.

---

### Post by SeijiSensei on 2010-10-28
By default in Ubuntu Postfix listens on all interfaces but only accepts mail sent through the localhost interface (127.0.0.1) so it's not an open relay.  See the "inet_interfaces" and "mynetworks" directives in /etc/postfix/main.cf.

These days, it would be professionally irresponsible to distribute an SMTP server whose default settings left it open to relaying.

---

### Post by Solignis on 2010-10-28
I see, so by opening it up to the internet for testing, I don't need to lose any sleep over it.

I would be adding my LAN to the networks does that change the fact.

Forgive me such basic questions, I am used to running hmail server on Windows which was very simple to setup considering it was GUI based.

---

### Post by HermanAB on 2010-10-29
Howdy,

Postfix is good if you are running an ISP with a few million users.  However, if you only have a few hundred users, then you could use Citadel.  It installs in about 20 minutes and does absolutely everything. It has been a well kept secret since about 1985:
[http://citadel.org](http://citadel.org)

---


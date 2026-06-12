---
title: "Lamp:"
date: 2007-03-12
forum: Server Platforms
---

### Post by edyson on 2007-03-12
I'd like to set up a simple lamp site. I've installed 6.06 LTS in server mode, installed apache2, mysql and php5 according to the instructions help.ubuntu.com. The only change I've made to the default config files is I added "UserDir public_html" to /etc/apache2/sites-available/default. 
I also cron'd apt-get update && apt-get upgrade. Assuming that the php scripts are secure, what else should I do before this server faces upwards?

---

### Post by Tichondrius on 2007-03-12
You don't need anything else, just make sure you it's behind a firewall, either an external one (e.g. hardware router) or a software firewall that you run on the same machine (e.g. firestarter)

---

### Post by gaten on 2007-03-12
You should read these articles:

Securing PHP:
[http://www.securityfocus.com/infocus/1706](http://www.securityfocus.com/infocus/1706)

Securing Apache2:
[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

Also use mod_chroot, its quick and easy and provides good security for your site.
[http://core.segfault.pl/~hobbit/mod_chroot/]("http://core.segfault.pl/%7Ehobbit/mod_chroot/")

---


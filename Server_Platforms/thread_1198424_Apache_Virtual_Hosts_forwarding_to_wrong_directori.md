---
title: "Apache Virtual Hosts forwarding to wrong directories"
date: 2009-06-27
forum: Server Platforms
---

### Post by unforeseen_incident on 2009-06-27
Hi everyone,

I've got an issue with apache,

I'm running the latest release of ubuntu server and apache and php.

I'm using webmin mainly to configure my virtual hosts.

Webmin says i have a default (catch-all) virtual host which is displayed at the top of the list of hosts.

I then have set up one for robmccann.co.uk and ipraise.co.uk (an old, old site of mine).

i have set the Server hostnames to pick up robmccann.co.uk and ipraise.co.uk respectivly

robmccann is located in /var/www/robmccann
ipraise is located in /var/www/ipraise

harold.dontexist.org is the DynDNS domain that the other domains point to.

All three domains (inluding the DynDNS one which has no virtual machine 'attached') point towards /var/www/robmccann event though the 'Document root directory' is set to the correct directory.

there are no .htaccess files present


I'd appreciate any help you can give, I've tried to provide as much info to make it as painless for you to do the great job you do in helping people like me!

With thanks!

RoB

---

### Post by unforeseen_incident on 2009-06-27
they seem to go to the first virtual server in the list... at the moment it's /var/www/ipraise

---

### Post by LepeKaname on 2009-06-29
I think this is almost the same question as in:

[http://ubuntuforums.org/showthread.php?t=1198547](http://ubuntuforums.org/showthread.php?t=1198547)

---


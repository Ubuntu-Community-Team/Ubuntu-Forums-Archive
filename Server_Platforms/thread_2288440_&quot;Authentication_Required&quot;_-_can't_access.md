---
title: "&quot;Authentication Required&quot; - can't access mediawiki"
date: 2015-07-27
forum: Server Platforms
---

### Post by qojop on 2015-07-27
MediaWiki    1.25.1
PHP    5.5.9-1ubuntu4.11 (apache2handler)
MySQL    5.5.44-0ubuntu0.14.04.1


I Just finished installing [my mediawiki]("http://www.qojop.org") on my home server, I've pointed my domain name to my server ip address and edited $wgServer but the site keeps saying "Authentication Required" and I can't even view the wiki. How do I make the wiki public and get rid of "Authentication Required" ?

---

### Post by TheFu on 2015-07-28
I don't know the answer, but I can list what I'd do to determine the cause.
a) I'd check the apache log files. Look for in both the access and error logs.  Any messages there?
b) I tried that site - nothing was returned.  I'd check that the router is setup to forward the port you intend to the static IP of the system on your LAN.
c) I would strongly caution against putting this onto the internet without carefully locking down the server and the web server and the php webapp AND the mysql DB.  Search for "security best practices" with each of the items in the software stack. Take careful notes and follow up on each item.
d) Check the firewall - it usually isn't running by default, but many guides would ask that it be configured. Double check that it is correct.

So ... I suspect either the router isn't configured correctly and it allows remote management - that's why a "Authentication Required" could be shown.
Or the permissions of the php engine and settings aren't correct so apache is refusing.  Apache has access controls which changed in 14.04 and later with apache 2.4.  The apache log files would show those errors.

Hope that helps.

---


---
title: "Apache Virtual Host Issue"
date: 2016-11-22
forum: Server Platforms
---

### Post by ndstate on 2016-11-22
Hello,

I run an Ubuntu server with Apache and have multiple websites set up via virtual hosts. For some odd reason Apache seemingly randomly "forgot" the document root for one particular URL and instead was forwarding all traffic to the default host. I was able to fix the issue by re-saving the correct folder directory and restarting Apache, but I would like to troubleshoot and figure out why it happened. Does anyone have any recommendations for figuring out why this occurred and what I should be looking for in the logs or what not?

Thank you.

---

### Post by SeijiSensei on 2016-11-22
I don't know why this would happen randomly.  The most likely reason for a virtual host failing to load is that host requested in the URL does not match exactly the ServerName or ServerAlias of some virtual host.  Apache decides which virtual host to use based on that matching.  If no configuration includes a matching ServerName, you get the default server with DocumentRoot /var/www/html.

---

### Post by Habitual on 2016-11-22
> **ndstate said:**
> Does anyone have any recommendations for figuring out why this occurred and what I should be looking for in the logs or what not?

Thank you.
Did the dns for the URI recently change?

---


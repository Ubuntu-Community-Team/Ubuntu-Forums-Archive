---
title: "Contents of PHP $_SERVER[HTTPS] with SSL"
date: 2006-08-14
forum: Server Platforms
---

### Post by igb on 2006-08-14
I have just set up a LAMP server with SSL and it all seems to be working OK. I can access my sites via both http and https. When I access the site via https I get the padlock symbol in Firefox and it is showing the correct certificate information.

I want to be able to detect if users are visiting the https or the http version of my site. If I examine the PHP variable $_SERVER[HTTPS] it empty for both the ordinary http and the https version of my site.

I have also tried using $_SERVER[SERVER_PORT] and this returns 80 for both the SSL and non SSL version of the site. I have added 443 to ports.conf and I know my server is listening on port 443, because I can connect via that port.

I suspect that this is an Apache configuration problem. Does anyone know how to configure Apache to return the correct strings in $_SERVER[SERVER_PORT and $_SERVER[HTTPS]?

Ian.

---


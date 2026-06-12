---
title: "ufw honeypot?"
date: 2012-02-17
forum: Security
---

### Post by mohrt on 2012-02-17
I get thousands of HTTP requests hunting for mysqladmin setup scripts, etc. It would be nice to throw them into the ufw deny list upon a probe to one of these files.

So, I'd like to make a honeypot PHP script that simply adds a client's IP address to the ufw deny list. Has anyone made something like this? The biggest hurdle would be getting the IP address added to ufw from PHP, and getting that list to survive a system restart. PHP obviously doesn't run as root, so an intermediary step may be necessary, such as storing a list of IPs, and a separate cron job checks this list and adds them to the ufw deny rules. The list also needs to be part of the ufw startup ruleset. Anyways, if someone has done this please point the way, thanks!

---

### Post by lisati on 2012-02-17
One option is to delete unnecessary files from your installation, and create a custom 404 error page ("file not found") that automatically updates the .htaccess file. That way, the bad bot gets a 404 error the first time they try to access files that they shouldn't and subsequently get a "403" error ("access denied").

---


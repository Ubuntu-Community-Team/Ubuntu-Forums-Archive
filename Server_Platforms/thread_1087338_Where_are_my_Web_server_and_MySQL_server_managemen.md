---
title: "Where are my Web server and MySQL server management tools?"
date: 2009-03-04
forum: Server Platforms
---

### Post by josephmo on 2009-03-04
I started out with the Ubuntu desktop package (64bit). Using the package installer, I installed the web server, as well as the MySQL server. It said that it installed them successfully (I think). So, I type [http://localhost](http://localhost) and I get the following message:

Not Found

The requested URL / was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

I re-installed. Same results. I cannot find the web server and the MySQL management tool (dashboard, etc.) on any of the menus. What am I doing wrong. Incidentally, when I install PHP or Perl, should I see a category (something like Programming Languages?)

Regards,
Joseph

---

### Post by BDNiner on 2009-03-05
A MySQL administrator tool and MySQL query browser should have installed. I believe they are in the tools menu, if not you can install them using add-remove programs or synaptic.

---

### Post by Brazen on 2009-03-05
Are you sure Apache is started?  I think it is set to start at boot, but does not get started immediatly after installation.  Try running this in a terminal:  "sudo /etc/init.d/apache start" and then try connecting to [http://localhost](http://localhost).

---

### Post by josephmo on 2009-03-05
> **Brazen said:**
> Are you sure Apache is started?  I think it is set to start at boot, but does not get started immediatly after installation.  Try running this in a terminal:  "sudo /etc/init.d/apache start" and then try connecting to [http://localhost](http://localhost).

The web server is starting, and it's giving me an error message:

Not Found

The requested URL / was not found on this server.
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch mod_perl/2.0.4 Perl/v5.10.0 Server at localhost Port 80

---

### Post by cariboo on 2009-03-05
Do you have an index.html file in /var/www?

Jim

---


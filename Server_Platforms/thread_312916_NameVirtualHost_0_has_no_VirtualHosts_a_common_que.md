---
title: "NameVirtualHost *:0 has no VirtualHosts a common question but hard to find answer"
date: 2006-12-05
forum: Server Platforms
---

### Post by Bill007 on 2006-12-05
Kia Ora 

Can any body tell me  why  im getting this 

root@production:/home/bill007# /etc/init.d/apache2 reload
 * Reloading apache 2.0 configuration...                                                                                                                     [Wed Dec 06 01:13:39 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
[Wed Dec 06 01:13:39 2006] [warn] NameVirtualHost *:0 has no VirtualHosts

Hmmmmmmm

Regards Bill007

---

### Post by chrisfay on 2006-12-05
> Can any body tell me why im getting this

This happens when you have a NameVirtualHost *: directive in your 000-default file and no virtual hosts are using the specified port.

For example, if you had NameVirtualHost *:443 listed, but no <VirtualHost *:443> than you would get that error. If you have NameVirtualHost *:0 in your file, you can either comment it out, change the '0' to a port you're actually using or don't specify a port at all.

---

### Post by rohnjeynolds on 2007-07-15
Here's why I got this message, and how I got rid of it.
I set up my first virtual hosts by copying the default vh file in /etc/apache2/sites-available, then editing the copied files for each of my virtual hosts. When I enabled them (sudo a2ensite [sitename]) and reloaded Apache (/etc/init.d/apache2 reload), I got the 'no virtual hosts' warning.
Of course, in copying the default vh file, I also copied the NameVirtualHost * directive at the top of the file into my vh files. Apache doesn't need that directive repeated. So I removed that line from all of my vh files, left it in the default file, and reloaded Apache. No more warning messages!
Hope that helps someone.

---

### Post by TANGUN on 2007-12-30
> **rohnjeynolds said:**
> Of course, in copying the default vh file, I also copied the NameVirtualHost * directive at the top of the file into my vh files. Apache doesn't need that directive repeated....Hope that helps someone.

That's exactly what I needed! It really helped me.

---


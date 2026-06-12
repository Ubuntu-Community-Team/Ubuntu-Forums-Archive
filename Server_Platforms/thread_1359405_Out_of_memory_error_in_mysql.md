---
title: "Out of memory error in mysql"
date: 2009-12-19
forum: Server Platforms
---

### Post by subnet_rx on 2009-12-19
I've got apache2 and mysql setup on my localhost for testing. I'm trying to install a cms to develop a site. The problem is, I keep getting this error:

[INDENT]Fatal error: Allowed memory size of 16777216 bytes exhausted (tried to allocate 81978 bytes) in /var/www/includes/database.mysql.inc on line 144[/INDENT]

I've tried increasing the allowed memory in my.cnf with no change in the error. I actually don't see a number in my.cnf that is close to 16MB.

---

### Post by craigp84 on 2009-12-19
Is it not whatever runtime (PHP?) your website is on thats exhausting it's memory?

PHP would be set by the max memory directive in php.ini 

Hope it helps

---

### Post by indispus on 2009-12-20
Your problem is related to your PHP memory limit settings.


You have two ways to get rid of the problem:
**1.** edit your PHP configuration file (php.ini) and set a higher **memory_limit**.
**2.** edit your PHP scripts and in order to tell 'PHP' to use more memory. For example, in the first lines of your scripts add **ini_set('memory_limit', '32M');**

Cheers!

---

### Post by kpholmes on 2010-01-03
is there anything wrong with just setting a higher limit? or is there a limit on how much memory you should dedicate?

---


---
title: "Run php file in crontab"
date: 2008-10-31
forum: Server Platforms
---

### Post by ripstar74 on 2008-10-31
Hi,
Is anyone able to help me please?

I have installed a php helpdesk on Ubuntu server. The helpdesk has a php file to check a pop3 mailbox for new tickets. If i run php /var/www/trellis/sources/pop3.php from a command prompt then the mailbox is checked and everything works.
However when i enter */5 * * * php /var/www/trellis/sources/pop3.php in a crontab it doesnt work.

---

### Post by lykwydchykyn on 2008-10-31
Try giving the full path to php.  To this day I don't quite comprehend how cron sets up environment variables, sometimes they work and sometimes not.

Also, check your /var/log/syslog file.  Cron jobs should leave some kind of log about running or attempting to run, and any error output.

---

### Post by vpsville on 2008-10-31
Try:

*/5 * * * * root /usr/bin/php /var/www/trellis/sources/pop3.php  >> /dev/null

---


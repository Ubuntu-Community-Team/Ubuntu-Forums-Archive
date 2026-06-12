---
title: "Took update, now virtual hosts down. Help!"
date: 2012-03-12
forum: Server Platforms
---

### Post by Heeter on 2012-03-12
Hi all,

I took in a couple of security updates, now my apache virtual hosting is not working.

This is an Ubuntu 11.04 with LAMP and postfix email server.

The apache default webpage is showing, but none of the 5 virtual domains are not working

Everything was working properly before the updates.

I have rebooted the server and restarted apache several times.

Please help, as I am at a loss.

Thanks

Heeter

---

### Post by nsnidanko on 2012-03-13
Basic troubleshooting starts with checking logs and googling errors around (if you find any):

check apache2 logs in the following directory
/var/log/apache2/
check syslog

Let us know what do you find.

---

### Post by Heeter on 2012-03-13
Hi, Thanks for your reply

There is no syslog file in that folder

There is a bunch of error.log,access.log & other_vhosts_access logs

I rebooted the server once more. Looks like my php is not working ([http://50.18.190.196/info.php](http://50.18.190.196/info.php))

I am trying to access, and it just downloads a file.

Thanks

Heeter

---

### Post by nsnidanko on 2012-03-13
check out latest error.log. As for syslog it is located in the /var/log directory

As for php not working most likely update broke apache mods. You need to enable mod php5

Run the following:
**sudo a2enmod php5**

And restart apache2:

**sudo service2 restart**

Hope it helps,
Naz

---

### Post by Heeter on 2012-03-13
Thanks, nsnidanko, It worked..


Heeter

---


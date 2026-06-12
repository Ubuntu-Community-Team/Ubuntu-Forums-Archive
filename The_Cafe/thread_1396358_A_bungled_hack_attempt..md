---
title: "A bungled hack attempt."
date: 2010-02-02
forum: The Cafe
---

### Post by lisati on 2010-02-02
The following log entries might be worth a laugh to those interested in servers and security, it appears to be a bumbling effort by someone in Korea to try to look at my machine:
```

[Mon Feb 01 23:27:58 2010] [error] [client *.*.*.*] File does not exist: /var/www/phpmyadmin/config
[Mon Feb 01 23:27:59 2010] [error] [client *.*.*.*] File does not exist: /var/www/pma
[Mon Feb 01 23:28:00 2010] [error] [client *.*.*.*] File does not exist: /var/www/admin/config
[Mon Feb 01 23:28:01 2010] [error] [client *.*.*.*] File does not exist: /var/www/dbadmin
[Mon Feb 01 23:28:02 2010] [error] [client *.*.*.*] File does not exist: /var/www/mysql/config
[Mon Feb 01 23:28:03 2010] [error] [client *.*.*.*] File does not exist: /var/www/php-my-admin
[Mon Feb 01 23:28:04 2010] [error] [client *.*.*.*] File does not exist: /var/www/myadmin
[Mon Feb 01 23:28:05 2010] [error] [client *.*.*.*] File does not exist: /var/www/PHPMYADMIN
[Mon Feb 01 23:28:06 2010] [error] [client *.*.*.*] File does not exist: /var/www/phpMyAdmin/config
[Mon Feb 01 23:28:07 2010] [error] [client *.*.*.*] File does not exist: /var/www/config
[Mon Feb 01 23:28:07 2010] [error] [client *.*.*.*] File does not exist: /var/www/phppgadmin
[Mon Feb 01 23:28:08 2010] [error] [client *.*.*.*] File does not exist: /var/www/phpmyadmin2
[Mon Feb 01 23:28:09 2010] [error] [client *.*.*.*] File does not exist: /var/www/phpMyAdmin2
[Mon Feb 01 23:28:10 2010] [error] [client *.*.*.*] File does not exist: /var/www/mail
[Mon Feb 01 23:28:11 2010] [error] [client *.*.*.*] File does not exist: /var/www/webmail

```

I'm not worried. 



(If someone out there thinks I should be, I'll be happy to continue in the server or security sections if necessary.)

---

### Post by blueshiftoverwatch on 2010-02-02
Why didn't the guy list all of the files from in your / directory and branch off from there to try and find whatever it is he was looking for instead of looking for specific files first?

---

### Post by evolution1979 on 2010-02-02
Probably because most likely he was a "typical" hacker in that he was used to windows.  He probably got into the system and just had no idea what to do from there so started randomly looking around hoping to get lucky.

---

### Post by Rhubarb on 2010-02-02
I get a few of these attempts on my web server as well.
I'm quite sure it's a bot (or botnet) trying to do this, or possibly a script-kiddie's attempt at trying to find exploits.

---

### Post by lisati on 2010-02-02
> **Rhubarb said:**
> I get a few of these attempts on my web server as well.
I'm quite sure it's a bot (or botnet) trying to do this, or possibly a script-kiddie's attempt at trying to find exploits.

I had a closer look at my system logs and found a handful from a different IP address earlier in the day. The "/var/www" bit was a bit of a giveaway for me (a relative noob at running a server) that they weren't likely to succeed. And spammers in Taiwan have tried (unsuccessfully) a number of times as well.

---

### Post by NightwishFan on 2010-02-02
Is there a GUI for checking firewall logs?

---


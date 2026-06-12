---
title: "Cron Jobs (total newbie)"
date: 2008-05-30
forum: Server Platforms
---

### Post by coops36 on 2008-05-30
Dear All, 

Server: Ubuntu 7.10
PHP5
Webmin: 1.400


I have a php file Testmail.php located in the the directory:

/var/www/mywebsite/newfolder/Testmail.php


I want to set up a Cron job to run this every 2 weeks or whatever, webmin's schedule seems pretty easy to understand. But the commands and syntax and permissions I just cant get my head 
round. 

In Webmins 'Scheduled Cron Jobs' There are some items to be filled in:

Execute Job As:
Active:
Command:
Input to command:
Description:

I have filled in the following:

Execute Job As: www-data
Active:Yes
Command:/var/www/mywebsite/newfolder/Testmail.php
Input to command:
Description:My Cron Job

When I run the Job: 

Output from command /var/www/mywebsite/newfolder/Testmail.php ..

/bin/sh: /var/www/mywebsite/newfolder/Testmail.php: Permission denied

So I changed the 'Execute Job As: www-data' to root

And I get the same message.

Any help would be appreciated.

Thanks

Coops

---

### Post by hyper_ch on 2008-05-30
(1) install php5-cli

(2) change the command to:
```

php /var/www/mywebsite/newfolder/Testmail.php

```

(3) try it on the command line as the user you want it to run as

---

### Post by coops36 on 2008-06-05
Sorry for not getting back, but this worked a treat thanks very much.

---

### Post by ajmc on 2011-03-17
I am using ubuntu server to host my apps.  Can you run a php script on using cronjobs? I'm quite worried because it might need a sudo command before it executes the script? I tried it on my appserver and nothing seems to work without the sudo command :( any ideas?

---

### Post by rubylaser on 2011-03-17
Just add it to root's crontab instead of yours.

```
sudo -i
crontab -e
```
That will run your script as root without needing sudo.

---


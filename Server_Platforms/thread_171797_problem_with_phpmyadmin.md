---
title: "problem with phpmyadmin"
date: 2006-05-07
forum: Server Platforms
---

### Post by Kyran1 on 2006-05-07
Hi all,
My problem is this. Apache2 works fine, php works fine, but phpmyadmin seems to have problems. I'm not sure quite how to config it. The page loads but askss for user and password. I changed the config from cookie to config but still can't seem to access the mod. I use wamp5 on my other pc and have tried cp the info from my windows machine (not the files, just typing the config info into the correct places on my linux machine) and seem to be getting no where. an error  come up (2002 server not responding) and talks about mysql socket possibly not correctly configured. I installed the basic ubuntu os and used the apt-get commands for apache2, php4, mysql and phpmyadmin. I was reading some info in the docs about apache mods and how to activate them. Is there anythig I might be possibly missing? on wamp5 when the auth is set to config, I am taken directly to the db setup page. I have tried just with the normal (defalt)setting and used username: root, with out password, because when I go to the config.inc of phpmyadmin it has root as the user and no password entered. What shall I do?

Thanks

kyran

---

### Post by jimwillsher on 2006-05-07
Have you configured your phpmyadmin config file fully? I have phpmyadmin wunning on Ubuntu with apache and all seems fine.

---

### Post by Kyran1 on 2006-05-07
well, how exactly do I do that? Shouldn't the dealt settings work as well?

---

### Post by Daremo on 2006-05-07
What you might be looking for is changing this setting in the config.inc.php file:
$cfg['Servers'][$i]['auth_type']     = 'config';    // Authentication method (config, http or cookie based)?

Change 'config' to 'http'. This will get the logon window to appear. Then you won't need to worry about the user and password settings in the config file. And allows flexability for other users that may need restricted access to use it also.

initially, there is not a config.inc.php file in the main phpmyadmin folder. There is a config.default.php file in the Libraries folder. Copy this file and rename it to config.inc.php and move to the main phpmyadmin folder. Then edit this file for you configuration setup.

I am not familiar with wamp5, however it sounds like XAMPP (apachefriends.org). This is a pre-built and pre-configured "package" of Apache, MySQL and PHP along with other stuff to make it work. Basically these packages have had all the setup done for you.
Hope this helps...

---

### Post by Kyran1 on 2006-05-07
Thanks all, i figured out what I did wrong......:oops: 

I installed everything except for the mysql-server!

I assumed that the server was part of the package with apache2. After installing the mysql-server package everything works.

Thanks again for all the replies.

Kayrin

---


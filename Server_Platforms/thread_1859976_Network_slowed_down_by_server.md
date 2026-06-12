---
title: "Network slowed down by server?"
date: 2011-10-14
forum: Server Platforms
---

### Post by KIAaze on 2011-10-14
Hi,

I set up an http fileserver for a friend of mine and now she's experiencing a network slowdown. The server is on a normal desktop PC connected to the router via cable.

/var/log/apache2/access.log shows the following:
```
203.141.11.140 - - [11/Oct/2011:02:16:52 +0100] "GET //mysqladmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:52 +0100] "GET //typo3/phpmyadmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:53 +0100] "GET //phpadmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:53 +0100] "GET //phpMyAdmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:54 +0100] "GET //phpmyadmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:55 +0100] "GET //phpmyadmin1/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:55 +0100] "GET //phpmyadmin2/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:56 +0100] "GET //pma/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:56 +0100] "GET //web/phpMyAdmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:57 +0100] "GET //xampp/phpmyadmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:58 +0100] "GET //web/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:58 +0100] "GET //php-my-admin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:59 +0100] "GET //websql/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:16:59 +0100] "GET //phpmyadmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:00 +0100] "GET //phpMyAdmin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:01 +0100] "GET //phpMyAdmin-2/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:01 +0100] "GET //php-my-admin/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:02 +0100] "GET //phpMyAdmin-2.2.3/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:02 +0100] "GET //phpMyAdmin-2.2.6/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:03 +0100] "GET //phpMyAdmin-2.5.1/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:04 +0100] "GET //phpMyAdmin-2.5.4/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:04 +0100] "GET //phpMyAdmin-2.5.5-rc1/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:05 +0100] "GET //phpMyAdmin-2.5.5-rc2/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:06 +0100] "GET //phpMyAdmin-2.5.5/ HTTP/1.1" 401 636 "-" "-"
203.141.11.140 - - [11/Oct/2011:02:17:06 +0100] "GET //phpMyAdmin-2.5.5-pl1/ HTTP/1.1" 401 636 "-" "-"

```
which looks like people searching for vulnerable services.

The only external services running are standard apache and SSH as far as I know.

The SSH log showed a lot of attack attempts, so I installed denyhosts now, which should reduce that a bit.

Is there a way to do something similar for people scanning for services available over apache?
Or is the network slowdown generally unavoidable?

edit:
Ok, easily found answer to my first question...:
[http://serverfault.com/questions/20667/equivalent-to-denyhosts-but-for-http-requests](http://serverfault.com/questions/20667/equivalent-to-denyhosts-but-for-http-requests)
[http://www.modsecurity.org/](http://www.modsecurity.org/)
[http://www.fail2ban.org/wiki/index.php/Main%5FPage](http://www.fail2ban.org/wiki/index.php/Main%5FPage)
[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

Just installed fail2ban. Will see how things go.
Any further suggestions welcome. :)

---

### Post by supremedalek on 2011-10-14
We use fail2ban here and it worths every minute you spend configuring it.

---


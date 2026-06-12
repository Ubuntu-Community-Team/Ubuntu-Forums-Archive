---
title: "whois.ripe.net"
date: 2008-08-06
forum: Security
---

### Post by micdhack on 2008-08-06
I would like to ask you about this weird thing am seeing in my server's ps faux.

```
root     11558  0.0  0.2 292436 19080 ?        Ss   Jul30   0:03 /usr/sbin/apache2 -k start
www-data  7145  0.0  0.0 294772  4700 ?        S    Jul31   0:00  \_ /usr/sbin/apache2 -k start
www-data  7504  0.0  0.0   3908   544 ?        S    Jul31   0:00  |   \_ sh -c whois 87.202.66.122 -h whois.ripe.net
www-data  7505  0.0  0.0  12388   832 ?        S    Jul31   0:00  |       \_ whois 87.202.66.122 -h whois.ripe.net
www-data 13259  0.0  0.0 294720  7984 ?        S    Jul31   0:00  \_ /usr/sbin/apache2 -k start
www-data 14094  0.0  0.0   3904   540 ?        S    Jul31   0:00  |   \_ sh -c whois 77.49.156.173 -h whois.ripe.net
www-data 14095  0.0  0.0  12384   824 ?        S    Jul31   0:00  |       \_ whois 77.49.156.173 -h whois.ripe.net
www-data  2811  0.0  0.0 148800  3320 ?        S    Aug03   0:00  \_ /usr/sbin/fcgi-pm -k start
www-data  2814  0.0  0.7 170308 60264 ?        S    Aug03   0:45  |   \_ /usr/bin/perl /usr/share/request-tracker3.6/libexec/mason_handler.fcgi
www-data 23055  0.0  0.1 295032 15440 ?        S    Aug03   0:00  \_ /usr/sbin/apache2 -k start
www-data 24434  0.0  0.0   3908   544 ?        S    Aug03   0:00  |   \_ sh -c whois 58.69.66.229 -h whois.ripe.net
www-data 24435  0.0  0.0  12380   816 ?        S    Aug03   0:00  |       \_ whois 58.69.66.229 -h whois.ripe.net
www-data 25706  0.0  0.2 296524 17732 ?        S    15:48   0:03  \_ /usr/sbin/apache2 -k start
www-data 26073  0.0  0.2 298308 19252 ?        S    16:15   0:01  \_ /usr/sbin/apache2 -k start
www-data 26143  0.0  0.2 296512 17436 ?        S    16:21   0:01  \_ /usr/sbin/apache2 -k start
www-data 26157  0.1  0.1 295112 16160 ?        S    16:26   0:02  \_ /usr/sbin/apache2 -k start
www-data 26158  0.0  0.1 295604 16116 ?        S    16:26   0:00  \_ /usr/sbin/apache2 -k start
www-data 26160  0.0  0.1 294900 15320 ?        S    16:26   0:00  \_ /usr/sbin/apache2 -k start
www-data 26437  0.0  0.2 297280 17692 ?        S    16:48   0:00  \_ /usr/sbin/apache2 -k start
www-data 26440  0.0  0.1 292724 12200 ?        S    16:49   0:00  \_ /usr/sbin/apache2 -k start
www-data 26441  0.0  0.1 294872 15152 ?        S    16:49   0:00  \_ /usr/sbin/apache2 -k start
www-data 26444  0.0  0.1 294860 15556 ?        S    16:50   0:00  \_ /usr/sbin/apache2 -k start

```
As you can see under the apache2 service there are some child services that ping whois.ripe.net.
Do i have to worry about some security problems?

---

### Post by Mordac85 on 2008-08-07
Yes, unless there's some reason for your system to be looking up ppl in Greece and the Philippines.  If there's no reason for a whois lookup to those locations then I'd recommend investigating further.

---

### Post by micdhack on 2008-08-07
Any ideas on how i am going to track this?

I figured that maybe i should look on /var/log/apache2/ logs and syslog also. Do i need to look anything else?

Also by trying to restart apache2 i had some strange errors..at first restart failed and by view ps faux i saw that all childs of apache2 with this whois.ripe.net was still running and i had to kill each one myself and then start apache2.

---

### Post by micdhack on 2008-08-08
I discovered that its one of the scripts that one of the sites are using and nothing to worry about although because script are experiencing timeouts and stuck the apache2 daemon cant be restarted normally unless they are killed first.

Thanks for the help

---


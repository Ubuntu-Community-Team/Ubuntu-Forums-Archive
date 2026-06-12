---
title: "Block PHP Injection attacks with fail2ban"
date: 2010-04-12
forum: Security
---

### Post by wattaman on 2010-04-12
Hi!
I'm trying to implement this method to block php injection attack using fail2ban: [here it is]("http://blogs.buanzo.com.ar/2009/04/fail2ban-filter-for-php-injection-attacks.html"), however I'm not sure it applies to Ubuntu.
You see, there's this filter that must be added to the fail2ban jail file:
[HTML][php-url-fopen]
enabled = true
port    = http,https
filter  = php-url-fopen
logpath = /var/www/*/logs/access_log
maxretry = 1
[/HTML]
... but the /var/www/* folder doesn't contain any logs, so I think theis path must be changed. The question is: with what?
Alos, from the source above, this is the php-url-fopen.conf file that must be created in the /etc/fail2ban/filter.d directory so the rule must function:
[HTML]# Fail2Ban configuration file
#
# Author: Arturo 'Buanzo' Busleiman <buanzo@buanzo.com.ar>
# Version 2
# fixes the failregex so REFERERS that contain =http:// don't get blocked
# (mentioned by "fasuto" (no real email provided... blog comment) in this entry:
# http://blogs.buanzo.com.ar/2009/04/fail2ban-filter-for-php-injection-attacks.html#comment-1489
#

[Definition]

# Option:  failregex
# Notes.:  regex to match this kind of request:
#
# 66.185.212.172 - - [26/Mar/2009:08:44:20 -0500] "GET /index.php?n=http://eatmyfood.hostinginfive.com/pizza.htm? HTTP/1.1" 200 114 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727)"
#
failregex = ^<HOST> -.*"(GET|POST).*\?.*\=http\:\/\/.* HTTP\/.*$

# Option:  ignoreregex
# Notes.:  regex to ignore. If this regex matches, the line is ignored.
# Values:  TEXT
#
ignoreregex = 
[/HTML]
Also from the source above, the explanation of the php injection attacks:
> Aren’t you just tired of the massive amount of PHP Remote Injection attacks registered in your access log? You know, the ones that look like this:

GET /index.php?n=http://eatmyfood.hostinginfive.com/pizza.htm?

Even if you secure your webserver, and set allow_url_fopen = false in php.ini, the attack is still annoying.

So, any ideas on this, please?

---

### Post by cdenley on 2010-04-13
The access log for the default is located at /var/log/apache2/access.log by default.

---

### Post by wattaman on 2010-04-13
> **cdenley said:**
> The access log for the default is located at /var/log/apache2/access.log by default.

So, I'm just guessing here: if there's already this configuration in the fail2ban jail file:
[HTML][apache-overflows]

enabled = true
port    = http,https
filter  = apache-overflows
logpath = /var/log/apache*/*error.log
maxretry = 2[/HTML]

... can we guess that the [php-url-fopen] should look like this:
[HTML][php-url-fopen]

enabled = true
port    = http,https
filter  = php-url-fopen
logpath = /var/log/apache*/*access.log
maxretry = 1[/HTML]
?!
Please confirm this. Thank you!

---

### Post by cdenley on 2010-04-13
I think that should work.

---

### Post by buanzo on 2010-04-14
Yes, it will work. In my personal case (I authored that filter) I use a /var/www/$SITENAME/{logs|htdocs} structure for websites I host, so it makes sense for me. Of course, you can use the default as desired :)

yours,
Buanzo.
:guitar:

---

### Post by wattaman on 2010-04-15
OK, B. Thanks for everything!

---

### Post by buanzo on 2011-05-26
No problem :)

Also, make sure the /etc/fail2ban/filter.d/php-url-fopen.conf file has THIS failregex:

```
failregex = ^<HOST> -.*"(GET|POST).*\?.*\=http\:\/\/.*\ HTTP\/1\..*$
```

If not, you might get false positives for people accessing your site through google translate.

Also, make sure you create an ignoreregex for every valid usage of somevariable=http:// blablah that you might have. it's a PITA, I know.

---

### Post by Lars Noodén on 2011-05-27
If you haven't done so already, there are four good steps you can take to actually prevent injection attacks.

1. Use regular expressions to validate all data 

2. Escape all risky characters

3. Use PREPARE and EXECUTE statements when working with databases

4. Use the APIs and their placeholders when working with databases

---


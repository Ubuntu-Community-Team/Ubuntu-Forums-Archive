---
title: "Basic Webbserver questions"
date: 2010-02-14
forum: Server Platforms
---

### Post by mac666 on 2010-02-14
Hey
Me and my friends have some webbsites. Right now we have our webbsite hosted and i cost quite alot in the end for all of us,
so we thought that we could open a webbserver all together, and now i have some questions that i would hope you could help me with :)
**Warning: As you will notice my english aint perfect. And i also want to warn you that ive only been using Ubuntu for some months and i only worked with gnome, no terminal/server editions...**

We will use apache / php / mysql etc etc and have around 10 different webbsites running.

How would we do this?;

[LIST=1]
[*]Would we have 10 different, or would we have 1 apache running?
"/user1/www" and "/user2/www"? How can they have different apache settings? 

[*]How will the DNS be made up? Im very lost when it comes to dnses... Could we ask a hosting company to point "www.usr1.com" towards my ip and a specified folder like 127.1.1.1/usr1/www?
If not: How to solve point the different DNSes to different webbservers? Or could we do this by ourself in our own "nameserver" or whats it called? Same for mails?

[*]Is ubuntu suiteble for this? Is it possible to make an account, for example usr1, that only can access his /home/ and nothing else via ftp, and make that his "default starting location"?.

[*]How diffcult is it to make a e-mail server? Is it possible to run microsoft exchange servers on ubuntu, without having to pay licence (or if thats illegal, i dont know), or does imap protocol work as well?

[*]Making PHP-scripts run bash commands for root, is it possible?

[/LIST]

---

### Post by Satoru-san on 2010-02-14
> **mac666 said:**
> 

[LIST=1]
[*]Would we have 10 different, or would we have 1 apache running?
"/user1/www" and "/user2/www"? How can they have different apache settings?
[/LIST]
Just one> **mac666 said:**
> 
[LIST=1]
[*]How will the DNS be made up? Im very lost when it comes to dnses... Could we ask a hosting company to point "www.usr1.com" towards my ip and a specified folder like 127.1.1.1/usr1/www?
If not: How to solve point the different DNSes to different webbservers? Or could we do this by ourself in our own "nameserver" or whats it called? Same for mails?
[/LIST]
You can install your own nameserver or you can use the one assigned by dhcp, you cannot have a different one for ever site.> **mac666 said:**
> 
[LIST=1]
[*]Is ubuntu suiteble for this? Is it possible to make an account, for example usr1, that only can access his /home/ and nothing else via ftp, and make that his "default starting location"?.
[/LIST]
Yes this is called Jailing and it can be done on servers such as VSFTPD> **mac666 said:**
> 
[LIST=1]
[*]How diffcult is it to make a e-mail server? Is it possible to run microsoft exchange servers on ubuntu, without having to pay licence (or if thats illegal, i dont know), or does imap protocol work as well?
[/LIST]
If you want email server make sure you have rDNS set up or you will be blacklisted. This also means you MUST have a static IP> **mac666 said:**
> 
[LIST=1]
[*]Making PHP-scripts run bash commands for root, is it possible?
[/LIST]

Possible to run commands with exec(); just cant do them as root unless apache is root o_O dont do that though. Best thing to run things as root is crontab

```
man crontab
```

---

### Post by mac666 on 2010-02-15
> **Satoru-san said:**
> Just oneYou can install your own nameserver or you can use the one assigned by dhcp, you cannot have a different one for ever site.Yes this is called Jailing and it can be done on servers such as VSFTPDIf you want email server make sure you have rDNS set up or you will be blacklisted. This also means you MUST have a static IP
Possible to run commands with exec(); just cant do them as root unless apache is root o_O dont do that though. Best thing to run things as root is crontab

```
man crontab
```

Thanks.

I can only have one DNS per IP?
Static IP wont be a problem.
Well, perhaps i dont need to run the commands as Root, but perhaps as a user with sudo? I was thinking of how the user could change his password with a webbif for his account on ubuntu!

How would the Apache setup work?
Would each user have a conf file?

---

### Post by Satoru-san on 2010-02-15
> **mac666 said:**
> Thanks.

I can only have one DNS per IP?
Static IP wont be a problem.
Well, perhaps i dont need to run the commands as Root, but perhaps as a user with sudo? I was thinking of how the user could change his password with a webbif for his account on ubuntu!

How would the Apache setup work?
Would each user have a conf file?
nope cant sudo to get root, apache would have to be in wheel and you would have to find a way to get around the entering the password part.

I am not sure on ubuntu server how it works, but you are looking for vhosts and you will add a block like this one.

```

<VirtualHost *:80>
        ServerName dont.fear.jp
        ServerAdmin mushwars@gmail.com
        DocumentRoot "/var/www/localhost/japan/htdocs/"

        <Directory "/var/www/localhost/japan/htdocs/">
            Options Indexes FollowSymLinks
            AllowOverride All
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule alias_module>
            ScriptAlias /cgi-bin/ "/var/www/localhost/japan/cgi-bin/"
        </IfModule>

        <Directory "/var/www/localhost/japan/cgi-bin/">
            AllowOverride None
            Options None
            Order allow,deny
            Allow from all
        </Directory>

        <IfModule mpm_peruser_module>
                ServerEnvironment apache apache
        </IfModule>
</VirtualHost>

```

---

### Post by stlsaint on 2010-02-15
i think it would be best if you and friends were to purchase a server (nothing fancy needed) and as stated above use vhosting for multiple websites. Mind you that each website must have a FQDN for hosting from 1 ip address and a above average internet connection as well for server will be good. Maybe consider something like [linode]("http://www.linode.com/") if you dont want to purchase server.

---

### Post by mac666 on 2010-02-15
Well,
we want to purchue a server.
 
What specs would you recommend?
Could it be a PC minus videocard and 16GB ram and a 10000 RPM disk?

---

### Post by hessiess on 2010-02-15
For security, make sure that you run PHP as the owner of the web root and have each web root owned by a different user. This can be done using suexec or mpm_itk.

If PHP is running as the same user as apache, it effectively means that all the files which it is serving have to be chmod 777,  which means that if one of your vhosts is compromised, they are ALL compromised. In addition to this, if you are selling hosting, any user can view and maby also edit other users files. Hacks like safe_mode do not solve this problem.

This page explains the problems quite well:
[http://blog.stuartherbert.com/php/2007/11/21/the-challenge-with-securing-shared-hosting/](http://blog.stuartherbert.com/php/2007/11/21/the-challenge-with-securing-shared-hosting/)

> 
What specs would you recommend?
Could it be a PC minus videocard and 16GB ram and a 10000 RPM disk?


Unless you are handling a LOT of traffic, which I would guess that you are not, any old bottom of the line system is massively overkill for a simple server. You will lickly hit a bottleneck in the bandwidth of your internet connection ages before computer performance starts to become a problem. ANY computer from about the last 8 years would be OK, buying anything powerful would be a complete waste of money. Setting up a RAID array for storage might be advantageous unless you have another backup mechanism.

---

### Post by mac666 on 2010-02-15
we have 1000/100 mbit at the server location. and perhaps more of our friends will join us, so we want to be prepared for the future...
 
But how about mail? Is it hard to make a server? Should that be a hole different server running the mail?

---

### Post by hessiess on 2010-02-15
> **mac666 said:**
> we have 1000/100 mbit at the server location. and perhaps more of our friends will join us, so we want to be prepared for the future...

Is this in a data centre or on a home connection, If its a home connection I would be extremely surprised if you actually had 1000 megabit of UPSTREAM bandwidth. The speeds you can get on a LAN are NOT the same as the speeds you can get on an internet connection.

Unless you are handling thousands of requests per second, which is  unlikely, you do not need much in the way of hardware to run a web server.

> 
But how about mail? Is it hard to make a server? Should that be a hole different server running the mail?
Yes, you can easily set up a mail server on the same machine.

---

### Post by Iowan on 2010-02-15
[Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") is an article I bookmarked on name-based virtual hosting.

---

### Post by mac666 on 2010-02-16
> **hessiess said:**
> Is this in a data centre or on a home connection, If its a home connection I would be extremely surprised if you actually had 1000 megabit of UPSTREAM bandwidth. The speeds you can get on a LAN are NOT the same as the speeds you can get on an internet connection.
 
Unless you are handling thousands of requests per second, which is unlikely, you do not need much in the way of hardware to run a web server.
 
 
Yes, you can easily set up a mail server on the same machine.
 
Its at my home with 1000 Downstream and 100 upstream, static ip. :)
but how long would 10 mb last? For email + webbserver with 20 sites? 
The sites arent Forums or anything, only basic flash/php sites...
 
Thanks for the Article, i will check it out later!

---


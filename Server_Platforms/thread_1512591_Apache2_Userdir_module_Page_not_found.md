---
title: "Apache2 Userdir module Page not found"
date: 2010-06-18
forum: Server Platforms
---

### Post by Fluxflixflex on 2010-06-18
Hi,
I just installed apache2 server on my ubuntu 10.04. It works fine (i get the "that works" page when i access to [http://localost/](http://localost/) and get no errors or warnings when i start apache.
However, the localhost/~florian returns a 404 not found.

I've enabled the userdir module 
```
a2enmod userdir
```and restarted the apache server 
```
[/ sudo /etc/init.d/apache2 startCODE]

i still get the not found page:

[CODE]
florian@florian-ubuntu:~$ tail -100 /var/log/apache2/error.log 
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Jun 18 13:36:05 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Fri Jun 18 13:36:20 2010] [error] [client 127.0.0.1] File does not exist: /var/www/~florian

```Is it normal that apache is looking for  /var/www/~florian instead of /home/florian/publuc_html ??
 /home/florian/public_html exists with chmod 755


 ```
florian@florian-ubuntu:~$ cat /etc/apache2/mods-enabled/userdir.conf 
<IfModule mod_userdir.c>
    UserDir enabled
        UserDir disabled root
    UserDir public_html

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit Indexes
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>
```


I read lot of stuff but i don't see what is wrong with my configuration.

Thanks for your help :popcorn:

---

### Post by Bachstelze on 2010-06-18
> **Fluxflixflex said:**
> 
```
sudo /etc/init.d/apache2 start
```


If that's really what you did then it's normal because you didn't restart Apache. You told upstart to only start it, and since it was already started, it did nothing, so you're still running the old config. What you should do is

```
sudo /etc/init.d/apache2 reload
```

to reload the config. No need to restart Apache altogether.

---

### Post by Fluxflixflex on 2010-06-19
Hi
thanks for your quick reply :)
unfortunately this did not work either. I feel a bit upset,  i don't see what i am missing. everything look ok to me but i still get this error.
DO you have any debug tips ?

thanks

---

### Post by Ryan Dwyer on 2010-06-19
I copied your config. My Apache service won't even start. It gives me this error:

```

Syntax error on line 2 of /etc/apache2/mods-enabled/userdir.conf:
UserDir "enable" keyword requires a list of usernames

```

...even though it says UserDir enabled like yours.

My previous config, which works, is:

```

UserDir public_html
UserDir disabled root

```

Remove the enabled line.

---

### Post by Fluxflixflex on 2010-06-20
hi,
thanks for your reply. Unfortunately that did not make any difference, so i decided to run a complete removal of apache2 packages and a re-installation. No more problem now.
Thank you all for your replies.

Florian

---


---
title: "Apache2 - HTTPS Issue"
date: 2018-03-25
forum: Server Platforms
---

### Post by vs-ruthless on 2018-03-25
Hi,

I've run into a really weird issue I cannot connect to my Laravel development web page locally, it redirects me to HTTPS, but I can access it from any other machine on the network. 


[LIST]
[*]Local machine -> [http://myproject.dev](http://myproject.dev) redirects to [https://myproject.dev](https://myproject.dev) 
[/LIST]

[LIST]
[*]Any other PC on my network -> [http://myproject.dev](http://myproject.dev) no issues works as it should. 
[/LIST]

My dev site is on my Ubuntu 16.04 Desktop where I have installed a LAMP server, I've been using it for a while now with no issues. Updated PC, got up next day and boom stopped working, at first I thought this was a Laravel issue but as I can access it from other machines and it work normally, then it must be something else.

Please note that localhost works as per normal and the logs haven't helped either.

Any ideas?

---

### Post by TheFu on 2018-03-27
Is myproject.dev in the /etc/hosts file and correct?  Probably not it, but ... 
Would be helpful if you posted the config files for both http and https virtualhosts too. Please use code tags.

---

### Post by vs-ruthless on 2018-03-28
Hi TheFu

Thank you for replying.

myproject.dev is in my /etc/hosts

```
/etc/hosts

127.0.0.1       localhost
127.0.1.1       ubdevpc

127.0.0.1       myproject.dev
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
/etc/apache2/sites-available/000-default.conf

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

```
/etc/apache2/sites-available/myproject.conf

<VirtualHost *:80>.

ServerName myproject.dev
ServerAdmin webmaster@localhost

# Your Custom folder
DocumentRoot /var/www/html/myproject/public/

<Directory /var/www/html/myproject/public>

Options Indexes FollowSymLinks
AllowOverride All
Require all granted

</Directory>

ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

It's really strange why it doesn't work on my local machine but works fine on both my other Ubuntu machines on the network.

---

### Post by TheFu on 2018-03-28
So, exactly where is the port 443 redirection coming from?
Are you running any browser addons that go https first?

---

### Post by vs-ruthless on 2018-03-28
Just Adblock on Firefox, I tried it in Chrome same issue.

---

### Post by TheFu on 2018-03-28
[https://laravel.com/docs/4.2/quick](https://laravel.com/docs/4.2/quick) - says that Laravel provides their own webserver. It doesn't use Apache.  Are you certain apache is involved?  What php processes are running  on the system?

At this point, I'm just guessing at different things to try.  No clue what the issue could be.

Lynx?  Dillo?
While it shouldn't matter, 
Try:
```
127.0.0.1       myproject.dev localhost

```  single line.

Also, in the default.conf file, put in a bogus ServerName.  

I know on Android v7 and later, chrome ignores the local DNS settings and uses 8.8.8.8 first. Some sort of security decision that cannot be overridden.  I don't use chrome on computers.

BTW, I have https-everywhere FF addon installed and routinely access internal websites here without HTTPS. They don't have any 443/tcp listeners when that happens.  Only run apache for toy stuff. Mostly use nginx, so I'm hardly an expert.  I don't see how apache would redirect without using a proxy or redirect clause.   Could it be as simple as the URL being remembered in that specific browser?  Does the browser change the HTTP --> HTTPS as you type?  If you put the URL into a text file, remove the S and copy/paste it back, do the same problem happen?  

Of course, have you looked at the apache log files for each site?  I specifically split my logs for each domain so it is clear which handler gets used.

Lastly, might be helpful to see what process is listening on 443 - I'd use **lsof** for that.

I'll assume you've cleared all the browser caches, correct?

---

### Post by vs-ruthless on 2018-04-01
Hi TheFu

Apologies for the delay in getting back to you, had a hetic few days.

I've managed to sort it, I removed the .dev off the end of the **ServerName** myproject.dev and I removed the trailing "/" off the end of the **DocumentRoot** /var/www/html/myproject/public/ and it started working.

I've not used Nginx I tend to stick with Apache, once my project is complete I should run a side by side comparison using my project.

Once again thank you for your help

---


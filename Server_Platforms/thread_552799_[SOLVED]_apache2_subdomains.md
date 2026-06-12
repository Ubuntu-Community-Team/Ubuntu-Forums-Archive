---
title: "[SOLVED] apache2 subdomains"
date: 2007-09-16
forum: Server Platforms
---

### Post by xIke on 2007-09-16
Hey all.

I'm trying to setup subdomains with apache2 on my box.  I have two virtual hosts set up in /etc/apache2/sites-enabled/ :

```

#tabs.conf: 
<VirtualHost *:80>
	DocumentRoot /var/www/tabs
	ServerName www.mydomain.org
	ServerAlias mydomain.org www.mydomain.org
</VirtualHost>

#wiki.conf:
<VirtualHost *:80>
	DocumentRoot /var/www/wiki
	ServerName wiki.mydomain.org
	ServerAlias wiki.mydomain.org
</VirtualHost>
```

The problem I'm having is that no matter what I type in, it all gets routed to [www.mydomain.org](www.mydomain.org).  If I disable tabs.conf, everything gets routed to [www.mydomain.org/wiki](www.mydomain.org/wiki).  This puzzles me too...why does the first one successfully show [www.mydomain.org](www.mydomain.org) when it's routing to the tabs directory, but the second one shows [www.mydomain.org/wiki?](www.mydomain.org/wiki?)

I'm clearly a noob and this is probably an obvious fix...I just don't know how else to diagnose this.  /var/log/apache2/error.log doesn't give any pertinent clues.

I have searched the forums and the help and found similar questions, but the answers were either really simple, or exactly what I'm already doing.

Thanks in advance,
xIke

---

### Post by Koybe on 2007-09-17
This is because your #tabs definition is the first encounter when parsing the config file. 

Did you set the NameVirtualHost directive? Have a look to the default config file /etc/apache2/sites-available/default ;)

---

### Post by xIke on 2007-09-17
The only thing in that file is

```
NameVirtualHost *
```

Is there a way to make #tabs catch mydomain.org, [www.mydomain.org](www.mydomain.org) #wiki catch wiki.mydomain.org, and have everything else error? (ideal would be to let me create a default domain where I could link to possible subdomains...)

---

### Post by Koybe on 2007-09-17
But you need that directive to enable virtuel hosting. So if your default site is not enable, you need to add NameVirtualHost * somewhere.

---

### Post by xIke on 2007-09-17
Pretend I'm an idiot and have no idea what you just said...  What are you saying I should do to fix this?

---

### Post by Brazen on 2007-09-18
try "sudo a2ensite default" then restart the apache service.

Or post the contents of /etc/apache2/sites-enabled/

---

### Post by xIke on 2007-09-18
Sites-Enabled:
```
lrwxrwxrwx 1 root root   36 2007-09-18 01:13 000-default -> /etc/apache2/sites-available/default
-rw-r--r-- 1 root root  143 2007-09-18 01:17 tabs.conf
-rw-r--r-- 1 root root  129 2007-09-16 22:54 wiki.conf
```

All that's in the default file that the symbolic link is point to is "NameVirtualHost *"

Thanks.

---

### Post by Koybe on 2007-09-18
OK Thanks. It's a lot more clear.

I had the same problem before but I can't remember the solution. I would :
Open the 000-default then telling him :
```
NameVirtualHost ip:80
```Then modify all virtual host matching this :
```

#tabs.conf: 
<VirtualHost ip:80>

#wiki.conf:
<VirtualHost ip:80>
```Where ip is your ip indeed ;)

I'm trying to remember why I add the same problem... ;)

---

### Post by xIke on 2007-09-18
Are you saying I should have my IP instead of *, or just pondering what you may have done to fix this yourself?

---

### Post by Koybe on 2007-09-18
I can't remember sorry. But yes you should try with your ip.

---

### Post by xIke on 2007-09-18
Doing that broke everything.  None of my sites loaded.

It seems like a horrible way to make it work anyway...I'm tying my config to a certain IP, and if that IP changes, I have to go back in and modify.  Also, it won't allow for multiple IP's on multiple NIC's.

---

### Post by mattskr on 2007-09-18
this is how mine is setup (all I changed was the domain names)

```
NameVirtualHost *:80

<VirtualHost *:80>
        
        DocumentRoot /var/www
 <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www/html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
</VirtualHost>

<VirtualHost *:80>
        ServerName sub1.domain.com
        DocumentRoot /var/www/sub1
</VirtualHost>

<VirtualHost *:80>
        ServerName sub2.domain.com
        DocumentRoot /var/www/sub2
</VirtualHost>
```

---

### Post by xIke on 2007-09-18
I don't understand...  Could you show what code goes in what files?

---

### Post by xIke on 2007-09-19
> **Koybe said:**
> I can't remember sorry. But yes you should try with your ip.

I got it working, thanks guys:

```
#/etc/apache2/sites-enabled/default
NameVirtualHost *:80

#/etc/apache2/sites-enabled/tabs.conf
<VirtualHost *:80>
   ServerName www.mydomain.org
   DocumentRoot /var/www/tabs
</VirtualHost>

#/etc/apache2/sites-enabled/wiki.conf
<VirtualHost *:80>
   ServerName wiki.mydomain.org
   DocumentRoot /var/www/wiki
</VirtualHost>
```

---

### Post by wit_ on 2007-11-28
Damn, thanks you guys!

I've somehow understood those .confs incorrectly but now with that simple instruction I got everything working like a charm :D

Great big thanks to you!

---


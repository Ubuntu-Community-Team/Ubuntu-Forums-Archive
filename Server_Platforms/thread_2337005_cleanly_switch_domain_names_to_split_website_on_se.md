---
title: "cleanly switch domain names to split website on server"
date: 2016-09-13
forum: Server Platforms
---

### Post by micahpage on 2016-09-13
So i have a server which hosts python-gaming.com and metulburr.com. I setup metulburr.com successfully to load in a different directory, but after installation of everything we want to change the domain name. However the installation of everything relies on the old path..so i dont want to change the path names at all. How can i point a new domain to where metulburr.com currently points. IF i point the domain to the IP address, it goes to the default of python-gaming.com which is at /var/www/html/. I want the new domain to point to /var/www/metulburr.com/ 

/etc/apache2/sites-enabled
```
<VirtualHost *:80>    
    ServerAlias www.metulburr.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/metulburr.com
    ServerName metulburr.com
    <Directory /var/www/metulburr.com>
        Order allow,deny
        Allow from all
    </Directory>




    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For th`e default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com




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




```
I tried just changing the ServerAlias to the new domain, and restarting apache but it didnt do anything?

---

### Post by newbie-user on 2016-09-13
So if I'm understanding correctly, you want to change the domain from metulburr.com to [newdomain].com? Just change the ServerName to [newdomain].com

---

### Post by micahpage on 2016-09-13
I did but its still pointing to the first website located on /var/www/html


```
<VirtualHost *:80>    ServerAlias www.python-forum.io
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/metulburr.com
    ServerName python-forum.io
    <Directory /var/www/metulburr.com>
        Order allow,deny
        Allow from all
    </Directory>



```

```
metulburr /etc/apache2/sites-enabled $ ls000-default.conf  metulburr.com.conf  python-forum.io.conf  python-forum.net.conf
metulburr /etc/apache2/sites-enabled $ sudo vim python-forum.io.conf 
[sudo] password for metulburr: 
metulburr /etc/apache2/sites-enabled $ sudo service apache2 reload
 * Reloading web server apache2
 * 
metulburr /etc/apache2/sites-enabled $ 
```

Its weird because my virutal host file metulburr.com.conf is working fine for metulburr.com domain, and is similar...but the python-forum.io.conf is not  redirecting it to the same place.

---

### Post by micahpage on 2016-09-13
Im not sure if this is helpful or not?

```
metulburr /etc/apache2/sites-enabled $ /usr/sbin/apachectl -SVirtualHost configuration:
*:80                   is a NameVirtualHost
         default server www.python-gaming.com (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost www.python-gaming.com (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost metulburr.com (/etc/apache2/sites-enabled/metulburr.com.conf:1)
                 alias www.metulburr.com
         port 80 namevhost python-forum.io (/etc/apache2/sites-enabled/python-forum.io.conf:1)
                 alias www.python-forum.io
         port 80 namevhost python-forum.io (/etc/apache2/sites-enabled/python-forum.net.conf:1)
                 alias www.python-forum.io
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex fcgid-proctbl: using_defaults
Mutex default: dir="/var/lock/apache2" mechanism=fcntl 
Mutex mpm-accept: using_defaults
Mutex fcgid-pipe: using_defaults
Mutex watchdog-callback: using_defaults
Mutex rewrite-map: using_defaults
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
Define: ENABLE_USR_LIB_CGI_BIN
User: name="www-data" id=33 not_used
Group: name="www-data" id=33 not_used
metulburr /etc/apache2/sites-enabled $ 



```

---

### Post by micahpage on 2016-09-13
I learned if i disable [COLOR=#000000][FONT=&quot]000-default.conf ALL domains go to my second site, and the first site is ignored. So i made a new vhost file for python-gaming.com and set it to go to the first site. And that worked. I dont know why but it appears everything is as i want it. python-gaming.com -> /var/www/html (first site) and python-forum.io -> /var/www/metulburr.com (second site)[/FONT][/COLOR]

---

### Post by darkod on 2016-09-14
It looks like you solved your issue but one question though: From the above it looks like you are checking and modifying only files in /etc/apache2/sites-enabled. Is that right?

Because the correct folder to work with apache sites config is /etc/apache2/sites-available. The sites-enabled contains just symlinks to the conf files in sites-available. You should do all your changes in sites-available.

---

### Post by micahpage on 2016-09-14
It looks to appear to work...but it does not.

You can login to metulburr.com but not python-forum.io ...however they are leading back to the same directory with apache. IF you check the page source under pytohn-froum.io it shows it in a frame? There is not suppose to be a frame at all?

---

### Post by darkod on 2016-09-14
Please post the content of /etc/apache2/sites-available folder and the content of the .conf files in it.

---

### Post by micahpage on 2016-09-14
I appreciate your help

---

### Post by micahpage on 2016-09-14
```
metulburr /etc/apache2/sites-enabled $ ls
metulburr.com.conf  python-forum.io.conf  python-gaming.com.conf
metulburr /etc/apache2/sites-enabled $ cd ../sites-available/
metulburr /etc/apache2/sites-available $ ls
000-default.conf  domain1.com.conf  metulburr.com.conf    python-forum.net.conf   wsgi.conf
default-ssl.conf  FlaskApp.conf     python-forum.io.conf  python-gaming.com.conf



```

content of apach config
```
metulburr / $ python codepad.py etc/apache2/apache2.conf 
The link:  http://codepad.org/Kni5J8XX


```
content of sites-available
```

metulburr / $ python codepad.py etc/apache2/sites-available/python-forum.io.conf 
The link:  http://codepad.org/z91iWKhE
metulburr / $ python codepad.py etc/apache2/sites-available/python-gaming.com.conf 
The link:  http://codepad.org/1YSa9sMz
metulburr / $ python codepad.py etc/apache2/sites-available/metulburr.com.conf 
The link:  http://codepad.org/9pduPJnt
metulburr / $ python codepad.py etc/apache2/sites-available/wsgi.conf 
The link:  http://codepad.org/eRrwwEcA
metulburr / $ python codepad.py etc/apache2/sites-available/FlaskApp.conf 
The link:  http://codepad.org/srU1TYvs
metulburr / $ python codepad.py etc/apache2/sites-available/domain1.com.conf 
The link:  http://codepad.org/ULzEjrKX
metulburr / $ python codepad.py etc/apache2/sites-available/default-ssl.conf 
The link:  http://codepad.org/c21AyyUD
metulburr / $ python codepad.py etc/apache2/sites-available/000-default.conf 
The link:  http://codepad.org/q1rPwOe4
metulburr / $ 



```

content of sites-enabled
```

metulburr / $ python codepad.py etc/apache2/sites-enabled/metulburr.com.conf 
The link:  http://codepad.org/FaSSLy1b
metulburr / $ python codepad.py etc/apache2/sites-enabled/python-forum.io.conf 
The link:  http://codepad.org/6N57sbtt
metulburr / $ python codepad.py etc/apache2/sites-enabled/python-gaming.com.conf 
The link:  http://codepad.org/Pth5IwXJ

```

I didnt know htat you were suppose to not edit sites-enabled at all

---

### Post by darkod on 2016-09-14
Are the folders /var/www/html and /var/www/metulburr.com owned by www-data?

---

### Post by micahpage on 2016-09-14
I am wondering if this might be a culprit and not apache? This is a screenshot of where we got the domain. Namecheap. And this is what namecheap support had us insert to point to the IP address of the server. I am wonering if the "redirect" part might be a reason as to why python-forum.io is going through an iframe?

[http://imgur.com/a/BAORM](http://imgur.com/a/BAORM)

EDIT:
They appear to be root?
```
metulburr /var/www $ ls -ltotal 192
drwxr-xr-x 23 root root 180224 Oct 13  2015 Dump
drwxr-xr-x  6 root root   4096 Oct 26  2015 ftp
drwxr-xr-x 11 root root   4096 Sep  9 08:58 html
drwxr-xr-x 14 root root   4096 Sep 14 16:37 metulburr.com



```

---

### Post by darkod on 2016-09-14
It doesn't open any image for me. You can simply attach the image here to a post, no need for external links.

Regardless where you got the domain name, if they at least offer basic DNS you could just set up A record pointing to the public IP of the webserver. That's all you need. No redirects of any kind...

---

### Post by micahpage on 2016-09-14
[IMG]http://imgur.com/a/BAORM[/IMG]
I am not sure why the BBCode is not showing the link...and that is the reason i put an external link

anyways the DNS is set to

```
URL REdirect REcord @ http://198.199.80.192:80 MAsked META
URL REdirect REcord www http://198.199.80.192:80 MAsked META
```

If i change it to 
> A Record @ 198.199.80.192 
i get a 400 error

---

### Post by micahpage on 2016-09-14
I believe the problem was due to putting redirect and not "A Record" in the domain of where it was pointing to.

---


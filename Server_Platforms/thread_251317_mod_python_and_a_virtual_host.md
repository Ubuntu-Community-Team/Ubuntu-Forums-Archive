---
title: "mod_python and a virtual host"
date: 2006-09-05
forum: Server Platforms
---

### Post by strider1551 on 2006-09-05
Hello all,

Here's my situation:
  -I have my apache2 server set up to use mod_python.
  -The server has a dynamic ip, so I use dyndns for a domain name.
  -The server is behind a router, which has the proper port forwarding.

Here's my problem:
  -Accessing index.py works from within the network.
  -Accessing index.py works from outside the network using my actual ip address.
  -Accessing index.py **does not** work from outside the network using my dyndns domain name.
Edit: I should note that by "does not work", firefox opens a save dialogue and saves the source code.

In my sites-enabled default file I have (amongst other things):
```

<VirtualHost *>
    ServerName mysite.selfip.com
    ServerAlias *.mysite.selfip.com
    DocumentRoot /var/www/mysite/html
    CustomLog /var/www/mysite/logs/access.log combined
    ErrorLog /var/www/mysite/logs/error.log

    <Directory "/var/www/mysite/html">
      AddHandler mod_python .py
      PythonHandler mod_python.publisher
      PythonDebug On
    </Directory>
</VirtualHost>

```

I did a quick "grep mod_python /var/log/apache2/error.log" and didn't see anything wrong.  Any thoughts?

---

### Post by sysops on 2006-09-05
I suppose you are using apache 2.x ..

if so, make sure the configuration file for this virtual host (/etc/apache2/sites-enabled) begins like this

NameVirtualHost *:80
<VirtualHost *:80>

    ServerName yoursite.tld
    ServerAlias [www.yoursite.tld](www.yoursite.tld) www

....

As far as the addhandler and pythonhandler directives are concerned, i'd be inclined to say they work best (reliably) when placed inside the global conf file (/etc/apache2/apache.conf). This option enables mod_python globally to all virtualhosts tho, so if you wish for mod_python to be operable for just this site try placing these directives outside the <directory></directory> tags.

To stop your *py  files from being downloaded, make sure your MIME database reflects their purpose and add something like the following to the local conf file to prevent direct access.

<Files ~ "^\.py">
    Order allow,deny
    Deny from all
</Files>

I haven't worked with mod_python much but isnt a 'SetHandler' directive necessary too? You ought to double-check.

---

### Post by strider1551 on 2006-09-05
Thanks for the correction with the virtual host configuration.  As you might guess, I don't have a large amount of experience with configuring apache.

I placed the mod_python directives in /etc/apache2/apache2.conf as well the <Files...> you recommended.  I then restarted apache2 via "sudo /etc/init.d/apache2 restart".  However, my problem still persists.  The python script executes as it should when accessed using the ip address, but downloads the source when using the domain name.

Side Note:
I did some research on mod_python's use of AddHandler and SetHandler.  It appears that either can be used with the primary effect being whether or not the extension .py is needed in the address bar.
[http://www.python.org/pycon/dc2004/papers/14/]("http://www.python.org/pycon/dc2004/papers/14/")

---

### Post by strider1551 on 2006-09-05
Ah! Some progress!

I was playing with things, and I discovered that "http://mysite.selfip.com/" gives me the source code, but "http://mysite.selfip.com/index" gives me my page.  Oddly enough "http://myip/" works.  Thus, my problem isn't with mod_python, but with how the virtual host handles that index.  Unfortunately, I have class in a moment so I can't work on it for a few hours.  Here's a summary if someone knows what I need to do:

[http://mysite.selfip.com/](http://mysite.selfip.com/)       - returns python code
[http://mysite.selfip.com/index](http://mysite.selfip.com/index)  - returns executed page
[http://myip/](http://myip/)                    - returns executed page
[http://myip/index](http://myip/index)               - returns executed page

---

### Post by strider1551 on 2006-09-05
Wow.  Somewhere in the last several hours I managed to fix my problem.  It took me just as long to realize it, though, because I wasn't clearing my browser's cache (i.e. I'm an idiot).  Oh well.  I suppose I'll never do that again.

For those who stumble into this looking for the answer to a similar problem, here's what ended up in my default sites-enabled config:
```

NameVirtualHost *:80
<VirtualHost *:80>
    ServerAdmin myemail@mysite
    ServerName mysite.selfip.com
    ServerAlias www.mysite.selfip.com www
    DocumentRoot /var/www/mysite/html
    CustomLog /var/www/mysite/logs/access.log combined
    ErrorLog /var/www/mysite/logs/error.log

    SetHandler mod_python
    PythonHandler mod_python.publisher
    PythonDebug On
</VirtualHost>

```

---


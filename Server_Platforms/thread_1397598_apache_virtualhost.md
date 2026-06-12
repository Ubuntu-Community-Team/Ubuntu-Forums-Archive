---
title: "apache virtualhost"
date: 2010-02-03
forum: Server Platforms
---

### Post by Carus on 2010-02-03
ok so we have this linux box at home, it currently hosts one site, my dads site he uses for some side business
i wanted to take advantage of this webserver at home,
i created a new file in sites-available with this
```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin mydadsemail
        ServerName carus.homelinux.com:80

        DocumentRoot /home/carus/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/carus/public_html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

i have dyndns pointing to this box with that domain
the only other entry is the default entry

and then i restarted apache, 
i get this
[Wed Feb 03 11:52:54 2010] [warn] NameVirtualHost *:0 has no VirtualHosts

but when i try to load the page it gives me some html placeholder of my dads business, he has his site in /var/www
and so i go to my public_html folder, but i get permission denied, i cant open the darn thing to look inside, so i did a sudo nano /home/carus/public_html/index.html
and that file wont show up on carus.homelinux.com

---

### Post by cdenley on 2010-02-03
First of all, you should not have a "NameVirtualHost" line for your new site configuration. Older releases had this line in the *default* site configuration, but this has been moved to ports.conf.

Secondly, once you make a site available by creating the configuration in sites-available, you have to enable it, which creates a link to the the file in sites-enabled.
```

sudo a2ensite mynewsite
sudo /etc/init.d/apache2 reload

```

If you're still having problems, post this output.
```

lsb_release -id
ls -l /etc/apache2/sites-enabled
cat /etc/apache2/sites-enabled/*

```

---

### Post by Carus on 2010-02-04
```
carus@www:~$ lsb_release -id
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
carus@www:~$ ls -l /etc/apache2/sites-enabled
total 0
lrwxrwxrwx 1 root root 36 2008-11-06 20:55 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 34 2010-02-03 11:13 carus -> /etc/apache2/sites-available/carus
carus@www:~$ cat /etc/apache2/sites-enabled/*
NameVirtualHost *
<VirtualHost *>
        ServerAdmin emailaddresshere
#       ServerName www.kyleprecisionarms.ca:80

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


<VirtualHost *>
        ServerAdmin emailaddresshere
        ServerName carus.homelinux.com

        DocumentRoot /home/carus/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/carus/public_html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
carus@www:~$

```

thats the commands
ya i ran the a2ensite carus and restarted apache

i cant access the public_html folder in my home directory also

---

### Post by pirateghost on 2010-02-04
> **Carus said:**
> ```
carus@www:~$ lsb_release -id
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
carus@www:~$ ls -l /etc/apache2/sites-enabled
total 0
lrwxrwxrwx 1 root root 36 2008-11-06 20:55 000-default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 34 2010-02-03 11:13 carus -> /etc/apache2/sites-available/carus
carus@www:~$ cat /etc/apache2/sites-enabled/*
NameVirtualHost *
<VirtualHost *>
        ServerAdmin emailaddresshere
#       ServerName www.kyleprecisionarms.ca:80

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


<VirtualHost *>
        ServerAdmin emailaddresshere
        ServerName carus.homelinux.com

        DocumentRoot /home/carus/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/carus/public_html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
carus@www:~$

```thats the commands
ya i ran the a2ensite carus and restarted apache

i cant access the public_html folder in my home directory also


i am not seeing where you tell your virtualhost what port to listen to.

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```that is a fairly default host config....notice the "VirtualHost *:80"?

as far as your home folder not being accessible, did you make it readable by www-data user?

---

### Post by Carus on 2010-02-04
> **pirateghost said:**
> i am not seeing where you tell your virtualhost what port to listen to.
that is a fairly default host config....notice the "VirtualHost *:80"?

as far as your home folder not being accessible, did you make it readable by www-data user?

i chmod'd the public_html to 755 and now i have access to it

if i add :80 to that line virtual host i get this error when i reload apache
```

[Wed Feb 03 23:11:35 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```
in ports.conf it says Listen 80

---

### Post by pirateghost on 2010-02-04
did you add the :80 to both virtualhosts?

---

### Post by Carus on 2010-02-04
both the entries in sites-available?

then i just get twice the errors
```
sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2   
                                                                                                                    [Wed Feb 03 23:27:14 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

[Wed Feb 03 23:27:14 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

```

---

### Post by cdenley on 2010-02-04
You should have "NameVirtualHost *:80" somewhere in your configuration, not "NameVirtualHost *". Either that, or you should define your virtualhosts with "<VirtualHost *>". The NameVirtualHost and VirtualHost should match. With hardy, I believe the NameVirtualHost should be at the top of /etc/apache2/sites-available/default. If not, post the output from this command:
```

grep NameVirtualHost /etc/apache2/*.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*

```

---

### Post by Carus on 2010-02-04
ok i put the :80 in the default file on namevirtualhost and reloaded
but the carus.homelinux.com still doesnt show anyone of my index.html index.htm default.htm in my home public_html folder

is there an option somewhere to override virtual hosts and just point everything to /var/www? i think i have everything setup right in my extra sites-available entry, i dont know why it isnt working

---

### Post by cdenley on 2010-02-04
> **Carus said:**
> 
but the carus.homelinux.com still doesnt show anyone of my index.html index.htm default.htm in my home public_html folder


What does it show? The wrong vhost? 403 error? 500 error? Does it get a server response? Run this on the server and post the output:
```

nc -z -v -w 5 carus.homelinux.com 80
echo -e "GET / HTTP/1.0\nHost: carus.homelinux.com\n"|nc 127.0.0.1 80

```

---

### Post by Carus on 2010-02-04
when i navigate in my browser to carus.homelinux.com i see some page for my dads website, the files i have in my public_html just say hello world, hellow world and hello worlds

```

carus@www:~$ echo -e "GET / HTTP/1.0\nHost: carus.homelinux.com\n"|nc 127.0.0.1
HTTP/1.1 200 OK
Date: Thu, 04 Feb 2010 17:20:27 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch
Last-Modified: Wed, 03 Feb 2010 18:18:20 GMT
ETag: "72003-c-47eb63e3a5300"
Accept-Ranges: bytes
Content-Length: 12
Connection: close
Content-Type: text/html

hello world

```

is what comes up

---

### Post by cdenley on 2010-02-04
Apache is working correctly, as your output indicates. Your browser is displaying a cached page from before you fixed the configuration. When a new request is sent to your server for the "carus.homelinux.com" hostname, it returns "hello world".

---

### Post by Carus on 2010-02-04
when i view [http://carus.homelinux.com](http://carus.homelinux.com) it doesnt show hello world
when i clear my cache, it still doesnt come up with it
and when i use a proxy ninjacloak.com
and when i use my iphone on the 3g network i dont even know where the file exists on the server except as old-index.html in /var/www/

---

### Post by cdenley on 2010-02-04
The only way I can think of for that to be possible is if the vhost configuration for carus.homelinux.com is configured for the incorrect network interface, which isn't the case looking at the configuration you previously posted. Are you sure carus.homelinux.com is resolving to the correct server?
```

ping -c 1 carus.homelinux.com
echo -e "GET / HTTP/1.0\nHost: carus.homelinux.com\n"|nc -v carus.homelinux.com 80
ifconfig|grep inet\ addr
wget -q -O - http://whatismyip.org/ && echo

```

---

### Post by Carus on 2010-02-04
your a genius!!!

i have 2 static ip's coming into our house, the carus.homelinux.com points to the wrong one!!

thank you soo much for your help

---


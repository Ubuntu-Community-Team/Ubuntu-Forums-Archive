---
title: "apache2 help with virtual hosts"
date: 2009-09-10
forum: Server Platforms
---

### Post by kylegio on 2009-09-10
first of yes i did run the search and read all threads relevant to me, still don't get what i think is a simple fix.

im using ubuntu server edition, apache2 with php5, everything is up to date newest 

i have a website working lets call it example.com

i would like to have lets say site2.example.com which has a different document path. 

my default file reads:
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
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

```




my new one reads something like this
```

<VirtualHost site2.example.com:80>
ServerAdmin webmaster@localhost
#We want to be able to access the web site using www.dev.example.com or dev.exa$
ServerAlias www.site2.example.com
DocumentRoot /home/site2/www
#we want specific log file for this server
CustomLog /var/log/apache2/site2.example.com-access.log combined
</VirtualHost>

```




the error on restarting apache reads
```

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
[Thu Sep 10 16:26:39 2009] [error] (EAI 2)Name or service not known: Could not resolve host name site2.example.com -- ignoring!
 ... waiting [Thu Sep 10 16:26:50 2009] [error] (EAI 2)Name or service not known: Could not resolve host site2.example.com -- ignoring!
   ...done.

```

of course i have replaced my domain with example.com. 
what  have i done wrong can anyone help?


thanks
kyle

---

### Post by wojox on 2009-09-10
Look here:

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by kylegio on 2009-09-10
> **wojox said:**
> Look here:

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

ive read that,
thanks but i still do not know what i need to do :S


i can get it to work by changing default from
```

<VirtualHost *:80>

```

to
```

<VirtualHost example.com:80>

```

and this seems to work out how i want it to, however on restart it spits the error
```

sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
[Thu Sep 10 17:09:29 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Thu Sep 10 17:09:30 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
   ...done.

```

---

### Post by X-Rated on 2009-09-10
Hi,
a few things you can try.

Make sure you have this directive global 
[B]NameVirtualHost *:80
[/B] 
Add this directive inside each VirtualHost
[B]ServerName [www.domain.com]("http://www.domain.com")
[/B] 
It looks like it's trying to resolve the fqdn. Add the fqdn into your **/etc/hosts** file.

See how that goes.

---

### Post by kylegio on 2009-09-11
> **X-Rated said:**
> Hi,
a few things you can try.

Make sure you have this directive global 
[B]NameVirtualHost *:80
[/B] 
Add this directive inside each VirtualHost
[B]ServerName [www.domain.com]("http://www.domain.com")
[/B] 
It looks like it's trying to resolve the fqdn. Add the fqdn into your **/etc/hosts** file.

See how that goes.


hey thanks for the reply, unfortunately as you can probably tell this is my first time trying to figure out virtual hosts, ive read as much as i can but im not really sure what you are suggesting i try :( if you can elaborate that would be great


thanks, 
kyle

---

### Post by kustomjs on 2009-09-11
here what u need:

<VirtualHost *:80>
ServerName yourdomain.com
DocumentRoot /var/www/xxxx/
</VirtualHost>

---


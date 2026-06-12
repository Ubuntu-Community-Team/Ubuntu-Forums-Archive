---
title: "Apache Virtual Hosts always displaying first site"
date: 2009-02-17
forum: Server Platforms
---

### Post by wwwerewolf on 2009-02-17
Could anyone give me a hand? I've got a ubuntu 8.10 server install with apache running and I've setup two virtual hosts (for a .com and a .ca). No matter what URL the users enter they always go to the first site, the .ca (it was originally the apache default site).

The .ca site is the main one, the only purpose of the .com site is to setup redirects to the main site.

/etc/apache2/sites-available/www.mysite.ca:
<VirtualHost *>
        ServerAdmin [email]techsupport@mysite.ca[/email]
        ServerName [www.mysite.ca](www.mysite.ca)
        ServerAlias mysite.ca

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
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

    #Let the webserver see another folder outside of the normal directories
    Alias /webimages2/ "/mnt/images/"
    <Directory "/mnt/images/">
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>




/etc/apache2/sites-available/www.mysite.com:
<VirtualHost *>
        ServerName  [www.mysite.com](www.mysite.com)
        ServerAlias mysite.com

        DocumentRoot /var/mysite.com/
</VirtualHost>



I disenabled the apache default site when I moved the conf file to [www.mysite.ca](www.mysite.ca)
I’ve tried both reloading and restarting the apache server.

I would greatly appreciate it if anyone can point out what I am missing.

---

### Post by Znupi on 2009-02-17
Try using <VirtualHost *:80> instead of <VirtualHost *> in both your files. I don't think Apache can listen on ALL ports :D. After that a simple
```
sudo apache2ctl restart
```
should do the job.

---

### Post by wwwerewolf on 2009-02-17
Thanks Znupi,
   Worked like a charm! :p
   I never would have caught that myself.

---

### Post by Znupi on 2009-02-18
I'm glad it worked :). What you should've done was check the Apache error logs. I'm sure you would have found pointers to the problem there :).

---


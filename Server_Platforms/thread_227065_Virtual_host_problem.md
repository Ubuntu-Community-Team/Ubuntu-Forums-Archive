---
title: "Virtual host problem"
date: 2006-08-01
forum: Server Platforms
---

### Post by ragdemai on 2006-08-01
Can somebody help, I have a problem with my virtual host, I'm hosting my webpage in my internal network, when I restart my apache2 it came out this
"* Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerN ame
[Tue Aug 01 17:50:21 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameV irtualHost address is not supported, proceeding with undefined results
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerN ame
[Tue Aug 01 17:50:22 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameV irtualHost address is not supported, proceeding with undefined results
                                                                                           [ ok ]"

I don't know what is going on, below is my Configuration :
==========================================================
NameVirtualHost *
<VirtualHost *:80>
        ServerName petracarbon
        ServerAlias hq.petracarbon.fix
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/Joomla/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
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

================END=======================================================
& also my index.php not working.

---

### Post by jordans on 2006-08-01
ok, there is a much easier way to do this. This is what sites-availble should look like.


NameVirtualHost *
<VirtualHost *:80>
  ServerName secondwebsite.com
  ServerAlias [www.secondwebsite.com]("http://www.secondwebsite.com/")
  DocumentRoot /var/www/secondwebsite
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
  ServerName firstwebsite.com
  ServerAlias [www.firstwebsite.com]("http://www.vashontechsupport.com/")
  DocumentRoot /var/www/firstwebsite/
  CustomLog /var/log/apache2/sitename.com-access.log combined
  ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
delete everything else, put copy this in, and change it so that it has your info. This has been the solution for everyone with problems so far.

---

### Post by ragdemai on 2006-08-01
Ok now i have another problem when i type in [http://localhost/](http://localhost/)
on my web browser turn up 404 Not Found & the link change to "http://localhost/installation/index.php"

---


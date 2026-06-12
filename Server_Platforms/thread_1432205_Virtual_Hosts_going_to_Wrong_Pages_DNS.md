---
title: "Virtual Hosts going to Wrong Pages? DNS?"
date: 2010-03-17
forum: Server Platforms
---

### Post by Mr_H on 2010-03-17
I have a problem that's confusing me and I haven't been able to find anything online to help.  Hope someone here can be of assistance.

My server is running Apache2 and has several websites on it, so there's a need for virtual hosts.  
When I go to 'MainWebsiteName.com', I get the main website page.  
When I Go to 'www.MainWebsiteName.com' I get the front page for a totally different virtual host (SecondarySite.com). It's the same secondary site everytime.

I'm pretty sure it's something I messed up, in a Virtual Host or a DNS, but I'll be darned if I can find out where.  Any suggestions on where I can start looking to find the cause of this problem? I'd greatly appreciate it.

Thanks
Jon

---

### Post by Vegan on 2010-03-17
Post the config files so we can see what the problem is.

---

### Post by Mr_H on 2010-03-17
Here you go..the two virtual hosts files for the two sites in question (all relevant data altered, yada yada..)

Thanks
Jon


MainWebsite Virtual Host Config File
```

NameVirtualHost 123.45.67.89:80
# MainWebSite Virtual Host
<VirtualHost 123.45.67.89:80>
        ServerAdmin webmaster@localhost
        ServerName MainWebsite.com
#       ServerAlias *.MainWebsite.com

        DocumentRoot /var/www/
        UserDir public_html

        <Directory />
                Options FollowSymLinks
                #AllowOverride None
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                #AllowOverride None
                AllowOverride All
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
        #AllowOverride None
       AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Secondary Website Virtual Host Config File
```

# SecondaryWebsite.com Virtual Host
<VirtualHost 123.45.67.89:80>
        ServerAdmin webmaster@localhost
        ServerName SecondaryWebsite.com
        ServerAlias *.SecondaryWebsite.com

        DocumentRoot /home/SecondaryWebsite/public_html


        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/SecondaryWebsite/pubic_html>
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




```

---

### Post by inphektion on 2010-03-17
can you do NameVirtualHost *:80

and if you ping from an external source mainwebsite.com vs [www.mainwebsite.com](www.mainwebsite.com) do you get different IP's or the same?

---

### Post by Mr_H on 2010-03-17
> **inphektion said:**
> can you do NameVirtualHost *:80


I'm assuming you mean putting this line in the MainWebSite virtual host at the very top, replacing *NameVirtualHost 123.45.67.89:80*?  I did that, reloaded apache and there was no difference.
I did get a number of warnings (VirtualHost 123.45.67.89:80 overlaps with VirtualHost 123.45.67.89:80, the first has precedence, perhaps you need a NameVirtualHost directive

> **inphektion said:**
> 
and if you ping from an external source mainwebsite.com vs [www.mainwebsite.com](www.mainwebsite.com) do you get different IP's or the same?


Both hosts actually do go to the same IP Address (I only have 1 IP for this server). Pinging [www.mainwebsite.com](www.mainwebsite.com) or mainwebsite.com doesn't give me different IPs.

Thanks for the suggestions.
Jon

---

### Post by inphektion on 2010-03-17
ah.  I didn't even realize you had one IP.  You have one IP but are trying to do IP based virtual hosting. you want name based.
So do 
```
NameVirtualHost mainwebsite.com:80
# MainWebSite Virtual Host
<VirtualHost mainwebsite.com:80>
        ServerAdmin webmaster@localhost
        ServerName MainWebsite.com
      ServerAlias www.MainWebsite.com
```

and then 
```
# SecondaryWebsite.com Virtual Host
<VirtualHost secondarywebsite.com:80>
        ServerAdmin webmaster@localhost
        ServerName SecondaryWebsite.com
        ServerAlias *.SecondaryWebsite.com
```

---

### Post by Mr_H on 2010-03-17
Thank you!  I knew it was something simple that I was missing.  I had those IP Addresses in the NameVirtualHost, that probably was throwing me off.  The problem appears to be solved now:)



> **inphektion said:**
> ah.  I didn't even realize you had one IP.  You have one IP but are trying to do IP based virtual hosting. you want name based.
So do 

*SNIP* 

---


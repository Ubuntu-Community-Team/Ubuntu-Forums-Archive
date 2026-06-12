---
title: "Apache2 error - subdomain"
date: 2011-11-13
forum: Server Platforms
---

### Post by spindler on 2011-11-13
I am having a very weird error. Normally I would not have a problem with my setup but this is outside of my understanding.

I have several websites on my Ubuntu server 11.10  with LAMP.  My websites look like this.

devel.mysite.com
devel2.mysite.com
[www.mysite.com](www.mysite.com)

I want to add another development website so I am adding a site:

devel3.mysite.com

I copied the virtual  host file from my other devel.mysite.com  and created a new virtual host.  The devel and devel2  sites have Drupal websites.   The new site will have a wordpress site.

My Problem:  When I access  devel3.mysite.com  I do not go to this website.  I end up at the [www.mysite.com](www.mysite.com).
 
Any idea why this would happen?    Again I just copied the virtual host server file from devel.mysite.com and altered it to point to my new folder. 

Thanks,

Spindler

---

### Post by dapperdanny77 on 2011-11-13
recheck your virtual host section within your added config - especially ServerName

---

### Post by volkswagner on 2011-11-13
Did you enable the site and restart apache?

```
sudo a2ensite siteFileName
```

```
sudo service apache2 restart
```

---

### Post by spindler on 2011-12-02
Yes I did these steps.  I actually have 6 different sites on my webserver so I have done this before. 

I actually think this is an apache2 error.   I only started getting this error when I upgraded to 11.10. 


For some weird reason the virtual host files do not point to the right location.   I am very careful to NOT use any wild cards  in my server name ( ie:  *.mysite.com)    because this has caused problems earlier in my install of 11.10

Are there any issues with the new build of apache2  for Ubuntu 11.10?

---

### Post by satanselbow on 2011-12-02
It might help if you posted the contents of your virtualhost conf file but my guess would be that you have forgotten to change the **<directory>** line to the true location of you new vhost or not added the new virtualhost to your **/etc/hosts** file.

Why do you think this would be an apache2 error? It is more likely a simple misconfiguration on your part... so quick to judge and apportion blame... :D

---

### Post by spindler on 2011-12-02
Normally I would agree with you but I take notes.   Then I follow my notes to make my life easy when I repeat the process of creating a new site. 

This is a fresh install of a NEW release of Ubuntu.   11.10 has had some fairly serious issues.  I had a lot of issues with how this version handles apache2.

Here is my virtual host file for your interest.

<VirtualHost *:80>
    ServerAdmin [email]me@mysite.com[/email]
    ServerName newdev.mysite.com
    ServerAlias newdev.mysite.com

    DocumentRoot /home/www/newdev
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /home/www/newdev>
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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by spindler on 2011-12-02
I do not have notes on how to reinstall apache2  without affecting all of my sites.   I notice that when I get issues like this I typically have to reformat my drive and reinstall Ubuntu.  This always solves my problem but is a fair amount of work.

Can someone give me step by step instructions on how to reinstall apache2?

Thanks

Spindler

---


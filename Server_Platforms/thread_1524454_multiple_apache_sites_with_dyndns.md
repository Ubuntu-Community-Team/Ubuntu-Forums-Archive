---
title: "multiple apache sites with dyndns"
date: 2010-07-05
forum: Server Platforms
---

### Post by paul555 on 2010-07-05
Hi all i want to ask how is it possible to serve multiple sites hosted in my computer with apache through dyndns.I am using ubuntu 10.04 and i had setup a dyndns domain as of mydomain.homelinux.org/ .Also i had setup a virtual host with the below configuration
```
<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName  www.drupal-site.com
ServerAlias drupal-site.com

DocumentRoot /home/pavlos/Temp/websites/drupal-site/htdocs
<Directory />
Options FollowSymLinks
        AllowOverride all
</Directory>
<Directory /home/pavlos/Temp/websites/drupal-site/htdocs/>
Options FollowSymLinks 
        AllowOverride all
        Order allow,deny
        allow from all
</Directory>

ScriptAlias /cgi-bin/ /home/pavlos/Temp/websites/drupal-site/cgi-bin/
<Location /cgi-bin>
            Options +ExecCGI
    </Location>


    # Logfiles
    ErrorLog  /home/pavlos/Temp/websites/drupal-site/logs/error.log
    CustomLog /home/pavlos/Temp/websites/drupal-site/logs/access.log combined

</VirtualHost>

```
My /etc/hosts file is:
```
127.0.0.1 localhost joomla-site.com drupal-site.com
127.0.1.1 medic
```
Now when i go to mydomain.homelinux.org outside of my lan i see the default site of apache.Any suggestions?

---

### Post by paul555 on 2010-07-07
Anyone? :sad:

---

### Post by mattc9305 on 2010-07-07
Yes, you can create 2 dyndns domains that are directed to your ip address.
 
Then in the config for the first site change the line 'Server Name' and 'Server Alias' to the domain that you want to use to access that site.
 
In the config file for the second site do the same but instead using the other domain you set up.
 
But when typing the domains in the 'Server Name' field do not use www. simply type the domain.  As it is free the URL for the websites will be (for example) "mydomain.homelinux.org" not ["www.mydomain.homelinux.org]("http://www.mydomain.homelinux.org")".
 
Also remember to forward port 80 so your site can be accessed.
 
Good Luck :)

---

### Post by mattc9305 on 2010-07-07
> **paul555 said:**
> Also i had setup a virtual host with the below configuration

 
But why have you set up the site with that domain when it is not the one you got from dyndns.com?

---


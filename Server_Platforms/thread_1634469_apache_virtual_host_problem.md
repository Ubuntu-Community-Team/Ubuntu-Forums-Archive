---
title: "apache virtual host problem"
date: 2010-11-30
forum: Server Platforms
---

### Post by paul555 on 2010-11-30
Hi all i have a strange problem with apache and virtual hosts. I setup my site but when i try to access it from firefox i get an access denied error (403) . 
```
Forbidden
You don't have permission to access / on this server.
Apache/2.2.16 (Ubuntu) Server at localhost Port 80
```

My config files are 

/etc/apache2/sites-enabled/pavlos.homelinux.org
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


/etc/hosts
```
192.168.1.112	pavlos-laptop	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost joomla-site.com drupal-site.com
::1	pavlos-laptop	localhost6.localdomain6	localhost6
127.0.1.1	pavlos-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


apache error log
```
[Tue Nov 30 16:19:06 2010] [crit] [client 127.0.0.1] (13)Permission denied: /home/pavlos/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

I don't understand why apache tries to access /home/pavlos/.htaccess as my DocumentRoot is /home/pavlos/Temp/websites/drupal-site/htdocs/
Any ideas?

---

### Post by James78 on 2010-12-01
I had this error once and fixed it, I forgot how though.... I know the problem isn't caused by it trying to read /home/user/.htaccess.. I think it might've been permissions related. What are your directory permissions, and does www-data have read access? An easy configuration is to have your entire user directory not readable by anyone buy your user, -rwxr-x--- (0750), then add the www-data user to your users group, and that'll give it read only access to your files, so Apache can read, your user can, and no one else can. It's how I have my server setup.

---


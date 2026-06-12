---
title: "apache virtualhosts problem after test upgrade"
date: 2008-12-02
forum: Server Platforms
---

### Post by juicymixx on 2008-12-02
Hey,

   I recently upgraded a machine to 8.10 to check it for problems with the software were working on, and I ran into this problem: the httpd.conf file was overwritten.   
In putting it back together I noticed that local virtual hosts don't seem to be responding correctly.
   For instance, on this machine if we go to:
[http://localhost/wiki](http://localhost/wiki)
an alias in the httpd.conf file correctly routes the request to it's correct place, and
[http://localhost/](http://localhost/) (or [http://192.168.1.3/](http://192.168.1.3/))
correctly goes to the "It worked!" page (indicated by the DocumentRoot directive)
On the same machine a virtual host for phptest has been set in the httpd.conf file:
```
NameVirtualHost *
<VirtualHost *>
   ServerName phptest
   DocumentRoot "/home/ttt/public-html/phptest"
</Virtualhost>
```
however going to:
[http://phptest/](http://phptest/)
takes me to the same place as localhost (the "It worked!" page)

I tried making modifications to the httpd.conf file, however it looks as if the DocumentRoot directive is being ignored within the VirtualHost directive.

I'm sure that something else must have gotten overwritten/changed in the update, but I can't for the life of me figure out what it is.

Here's my httpd.conf file:
```
ServerName TestServer
DocumentRoot "/var/www"
NameVirtualHost *
<VirtualHost *>
   ServerName phptest
   DocumentRoot "/home/ttt/public-html/phptest"
</Virtualhost>
# Alias for wiki
Alias /wiki "/var/www/wiki/"
<Directory "/var/www/wiki/">
       Options Indexes FollowSymLinks MultiViews ExecCGI
       AllowOverride All
       Order allow,deny
       Allow from all
</Directory>
```

also, here's my /etc/hosts file:
```
127.0.0.1       localhost
127.0.0.1       phptest
192.168.1.3     TestServer
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks!

---

### Post by cdenley on 2008-12-02
/etc/apache2/httpd.conf should not be used. It is only there for backwards compatibility. Delete everything in there. For your "phptest" vhost, create this file

/etc/apache2/sites-available/phptest
```

<VirtualHost *:80>
        ServerName phptest
        DocumentRoot /home/ttt/public-html/phptest/
</VirtualHost>

```
then enable it, and reload
```

sudo a2ensite phptest
sudo /etc/init.d/apache2 reload

```

You want your default vhost's root to be "/var/www", correct? Why would you create an alias /wiki for /var/www/wiki? Isn't that where it would point anyway? If you want to edit your default vhost configuration, it is in /etc/apache2/sites-available/default.

---


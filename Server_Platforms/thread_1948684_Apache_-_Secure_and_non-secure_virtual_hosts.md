---
title: "Apache - Secure and non-secure virtual hosts?"
date: 2012-03-28
forum: Server Platforms
---

### Post by radhunter on 2012-03-28
Hello everyone! I am semi new to Linux, but still get stumped once in awhile. I would like to learn more about Linux than I know. I use it at work, and I'm currently working on a BS degree in IT. I learned a ton by being an active member of another forum, and hope I can do the same here! ):P

I am currently working on a non production Linux 11.10 server...

I have it setup with three virtual hosts, one static IP and three internal host names that map to this server. 


I have the virtual hosts working just fine, but where I am getting stumped is that I would like what I have designated as the primary virtual to be secure, and the other two not.

It works...kind of. The primary virtual host works as a secure virtual host, and the other two work as non secure virtual host. However, the problem I am running into is that I can put https: infront of the other two virtual hosts and they all go to the primary virtual host.

I understand that there is limitations on https with name based virtual hosts, from what I understand from googling is that you can have as many named based virtual hosts as you would like on a server, but only one secure host.

So I guess my question is would it be possible to have the other virtual hosts reject the https request and only serve requests on 80, and leave the primary virtual host to only serve secure requests?


Here is the configuration for my default(primary) vhost:

```
 <VirtualHost *:443>
        ServerAdmin webmaster@localhost
        ServerName derek.lib.byu.edu
        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateFile /var/www/server.crt
        SSLCertificateKeyFile /var/www/server.key
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```Here is the configuration file for the second vhost:

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost1
        ServerName xxx.xxx.xxx.xxx
        DocumentRoot /var/vhost1


        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/vhost1>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```And the third

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost2
        ServerName xxx.xxx.xxx.xxx
        DocumentRoot /var/vhost2
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/vhost2/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```httpd.conf
```

ServerName localhost
Listen 443

```ports.conf
```

 If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80

Listen xx.xx.xx.xxx:80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    #Listen 443 https
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

Any ideas?

---

### Post by Bachstelze on 2012-03-29
You can't just make the server not respond. Since you have only one vhost on port 443, all requests on port 443 are served by it. One thing you can do is create a 443 vhost for your other sites, and just make it redirest to the http version.

---

### Post by zeljkojagust on 2012-03-29
I'm not exactly sure what is you problem, so here is couple points of interest that you might find useful. 
 
[Linode]("http://library.linode.com/") has great community library that covers many Apache and SSL topics, and for multiple SSL VHosts on Apache check this one: [http://www.techrepublic.com/blog/opensource/configure-apache-to-support-multiple-ssl-sites-on-a-single-ip-address/987](http://www.techrepublic.com/blog/opensource/configure-apache-to-support-multiple-ssl-sites-on-a-single-ip-address/987)

---

### Post by radhunter on 2012-03-29
> **Bachstelze said:**
> You can't just make the server not respond. Since you have only one vhost on port 443, all requests on port 443 are served by it. One thing you can do is create a 443 vhost for your other sites, and just make it redirest to the http version.


Thats a great idea! I will try that, and then post how I did it!

---

### Post by radhunter on 2012-03-30
New problem....

I couldn't figure out how to use the mod_rewrite function.

But I think I've got a bigger problem.

The non secure host name for the default virtual host(host 1) redirects to the second virtual host. e.g. 

http://virtualhost1->virtualhost2


When you type in the secure [https://virtualhost1](https://virtualhost1) it goes to virtualhost1.

When you type in the https:// in front of any of the other virtualhosts:

https://virtualhost2->virtualhost1
https://virtualhost3->virtualhost1

they all redirect to the default virtual host...


Any ideas?

---


---
title: "Apache virtual hosts"
date: 2008-10-02
forum: Server Platforms
---

### Post by botfish on 2008-10-02
Hi,

I have done a fresh install of Ubuntu 8.04 server and it was working ("It works!"). Now I've been trying all night to setup virtual hosts.

I am getting the following errors:

user@server:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Oct 02 23:44:23 2008] [warn] NameVirtualHost 127.0.0.1:80 has no VirtualHosts
[Thu Oct 02 23:44:23 2008] [warn] NameVirtualHost 127.0.0.1:443 has no VirtualHosts
[fail]

My server ip address is 192.168.1.104
My desktop ip address is 192.168.1.103

On my desktop my hosts file is:
127.0.0.1	localhost
127.0.0.1	desktop
192.168.1.104	server

I have not touched the hosts file on my server.

I have a2dissite default

And created /etc/apache2/sites-available/test followed by a2ensite test

Contents of test:

#NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName test.local

        DocumentRoot /var/www/test/htdocs
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/test/htdocs>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/test/cgi-bin/
        <Directory "/var/www/test/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
               allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/test/cgi-bin/
        <Directory "/var/www/test/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/www/test/logs/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/www/test/log/access.log combined
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

In /etc/apache2/apache2.conf I have added:

NameVirtualHost 127.0.0.1:80
NameVirtualHost 127.0.0.1:443

When the above two lines are commented out I get the following error:

user@server:/etc/apache2$ sudo /etc/init.d/apache2 start
 * Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Any help would be appreciated.

---


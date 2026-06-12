---
title: "Apache Server troubleshooting"
date: 2011-05-11
forum: Server Platforms
---

### Post by lorewap3 on 2011-05-11
I'm having issues getting apache to respond to requests outside of my local LAN. If I goto my server URL ([http://www.poillion.com](http://www.poillion.com)) it says connecting... but never finishes and returns anything.

I'm using Ubuntu Server 10.10.

a) The DNS is working fine. It's pointed to my cable modem's IP and ping responds fine.
b) The apache server is setup and is working locally. In fact, if I use w3m and goto [www.poillion.com]("http://www.poillion.com") I reach the test page perfectly. 

I can't figure out where the missing piece is to close this gap. Here are some config files to illustrate my setup:

hostname
> poillion/etc/apache2/httpd.conf
> ServerName poillion/etc/hosts
> 
127.0.0.1       localhost
127.0.1.1       poillion
(along with ipv6 ones)

Note: I had my LAN IP and cable modem IP both setup in here as [www.poillion.com]("http://www.poillion.com") and that didn't work.

/etc/apache2/sites-available/poillion
> 
<VirtualHost *:80>
        ServerName [www.poillion.com]("http://www.poillion.com")

        ServerAlias *.poillion.com
        ServerAlias *.willpoillion.com

        ServerAdmin [EMAIL="will@poillion.com"]will@poillion.com[/EMAIL]

        DocumentRoot /home/www
        <Directory />
                Options -FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/www/>
                Options +Indexes +SymLinksIfOwnerMatch +MultiViews +ExecCGI
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>


        ErrorLog ${APACHE_LOG_DIR}/poillion_error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel debug

        CustomLog ${APACHE_LOG_DIR}/poillion_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Any help diagnosing would be greatly appreciated! Thanks!

Will

---

### Post by volkswagner on 2011-05-11
Getting connection timeout here.

Are you sure your port 80 is not blocked?  From inside your LAN navigate to canyouseeme.org and check port 80.  Possibly your isp is blocking or you have other hardware/software firewall.

---

### Post by Lars Noodén on 2011-05-12
From where I am, it looks like you are blocking ports 80 and 443 at the firewall.  Check to be sure those two ports are [open](http://www.canyouseeme.org/) and being forwarded to your web server.

---


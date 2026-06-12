---
title: "Can't get https to work with fresh installation of Apache and TomEE."
date: 2017-08-08
forum: Server Platforms
---

### Post by sethanath2 on 2017-08-08
Hi,

I have just performed a fresh installation of Ubuntu Server 16.04.3 LTS. However, I can't get https to work with Apache and Tomcat (TomEE)/8.5.6 (7.0.2).
Here are the steps that I have done.

1. Install Let's Encrypt Client
sudo add-apt-repository ppa:certbot/certbot
sudo apt update
sudo apt install python-certbot-apache

2. Set Up two SSL Certificates.
sudo certbot --apache -d zethanath.tk
sudo certbot --apache -d [www.zethanath.tk]("http://www.zethanath.tk")

3. Install and Configure mod_jk
sudo apt update
sudo apt install libapache2-mod-jk
sudo nano /etc/libapache2-mod-jk/workers.properties
   Find the workers.tomcat_home directive. Set this to your Tomcat installation home directory. For my Tomcat installation, that would be /opt/tomcat:
   ```
workers.tomcat_home=/opt/tomcat
```

4. Adjust the Apache Virtual Host to Proxy with mod_jk
 sudo apache2ctl -S
 
```
VirtualHost configuration:
*:443                  is a NameVirtualHost
         default server zethanath.tk (/etc/apache2/sites-enabled/000-default-le-ssl.conf:2)
         port 443 namevhost zethanath.tk (/etc/apache2/sites-enabled/000-default-le-ssl.conf:2)
         port 443 namevhost www.zethanath.tk (/etc/apache2/sites-enabled/000-default-le-ssl.conf:42)
*:80                   is a NameVirtualHost
         default server zethanath.tk (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost zethanath.tk (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost www.zethanath.tk (/etc/apache2/sites-enabled/000-default.conf:37)
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www/html"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex watchdog-callback: using_defaults
Mutex proxy-balancer-shm: using_defaults
Mutex rewrite-map: using_defaults
Mutex ssl-stapling-refresh: using_defaults
Mutex ssl-stapling: using_defaults
Mutex proxy: using_defaults
Mutex ssl-cache: using_defaults
Mutex default: dir="/var/lock/apache2" mechanism=fcntl 
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
User: name="www-data" id=33
Group: name="www-data" id=33
```

sudo nano /etc/apache2/sites-enabled/000-default-le-ssl.conf

[HTML]<IfModule mod_ssl.c>
<VirtualHost *:443>
        ServerName zethanath.tk
        #DocumentRoot /var/www/html

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk-0001/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk-0001/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

</VirtualHost>

<VirtualHost *:443>
        ServerName www.zethanath.tk

        #DocumentRoot /var/www/html

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/www.zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/www.zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

</VirtualHost>
</IfModule>[/HTML]

sudo nano /etc/apache2/sites-enabled/000-default.conf

[HTML]<VirtualHost *:80 >
        ServerName  zethanath.tk

        Redirect permanent "/" "http://192.168.1.70:8080/index.jsp"

        ServerAdmin xxx@xxx.com
        #DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        JKMount /* ajp13_worker

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
RewriteEngine on
RewriteCond %{SERVER_NAME} =zethanath.tk
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

<VirtualHost *:80 >
        ServerName  www.zethanath.tk

        Redirect permanent "/" "http://192.168.1.70:8080/index.jsp"

        ServerAdmin xxx@xxx.com
        #DocumentRoot /var/www/html

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        JKMount /* ajp13_worker

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
RewriteEngine on
RewriteCond %{SERVER_NAME} =zethanath.tk
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
[/HTML]

sudo apache2ctl configtest
Syntax OK

sudo systemctl restart apache2

Now, I would test each url of mine in Firefox.

1. I typed [http://zethanath.tk](http://zethanath.tk) and I would get the following.

[https://zethanath.tk/](https://zethanath.tk/)
Unable to connect

Firefox can’t establish a connection to the server at zethanath.tk.

    The site could be temporarily unavailable or too busy. Try again in a few moments.
    If you are unable to load any pages, check your computer’s network connection.
    If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.

2. I typed [http://www.zethanath.tk](http://www.zethanath.tk) and I would get the following, which is not what I want.

[ATTACH=CONFIG]276314[/ATTACH]


3. What I really want is this -> Redirect permanent "/" "http://192.168.1.70:8080/index.jsp"

[ATTACH=CONFIG]276315[/ATTACH]

Please note that I am working from my PC, which is remote to Ubuntu Server, without any configuration in /etc/hosts

```
127.0.0.1       localhost
127.0.1.1       erick-ASRock-N68C-GS4-FX

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Thank you.

---

### Post by sethanath2 on 2017-08-08
Here is a little more detail from TomEE. Please note that I have index.jsp, not index application.

cd /opt/tomcat/conf
sudo nano web.xml

...
    <welcome-file-list>
        <!-- <welcome-file>index/greet</welcome-file> -->
        <!-- <welcome-file>index.html</welcome-file> -->
        <!-- <welcome-file>index.htm</welcome-file> -->
        <welcome-file>**index.jsp**</welcome-file>
        <!-- <welcome-file>admin.jsp</welcome-file> -->
    </welcome-file-list>

</web-app>

Thank you.

---

### Post by sethanath2 on 2017-08-09
Please excuse this post of mine as I made mistake on it.

Thank you so much.

---


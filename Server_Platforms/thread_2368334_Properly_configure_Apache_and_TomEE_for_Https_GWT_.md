---
title: "Properly configure Apache and TomEE for Https GWT application."
date: 2017-08-09
forum: Server Platforms
---

### Post by sethanath2 on 2017-08-09
Hi,

I would like to learn how to properly configure Apache2 and Tomcat (TomEE)/8.5.6 (7.0.2) for GWT https application on fresh installation of Ubuntu Server 16.04.03.
Here are the steps that I used.

1. Configured my DNS records.

[ATTACH=CONFIG]276330[/ATTACH]

2. Checked Apache configuration.

sudo apache2ctl -S

```
VirtualHost configuration:
*:80                   zethanath.tk (/etc/apache2/sites-enabled/000-default.conf:1)
*:443                  is a NameVirtualHost
         default server zethanath.tk (/etc/apache2/sites-enabled/000-default-le-ssl.conf:2)
         port 443 namevhost zethanath.tk (/etc/apache2/sites-enabled/000-default-le-ssl.conf:2)
                 alias www.zethanath.tk
                 alias servlet.zethanath.tk
         port 443 namevhost zethanath.tk (/etc/apache2/sites-enabled/default-ssl.conf:2)
         port 443 namevhost www.zethanath.tk (/etc/apache2/sites-enabled/default-ssl.conf:140)
ServerRoot: "/etc/apache2"
Main DocumentRoot: "/var/www/html"
Main ErrorLog: "/var/log/apache2/error.log"
Mutex rewrite-map: using_defaults
Mutex ssl-stapling-refresh: using_defaults
Mutex ssl-stapling: using_defaults
Mutex proxy: using_defaults
Mutex ssl-cache: using_defaults
Mutex default: dir="/var/lock/apache2" mechanism=fcntl 
Mutex watchdog-callback: using_defaults
Mutex proxy-balancer-shm: using_defaults
PidFile: "/var/run/apache2/apache2.pid"
Define: DUMP_VHOSTS
Define: DUMP_RUN_CFG
User: name="www-data" id=33
Group: name="www-data" id=33
```

3. Configured my /etc/apache2/sites-enabled/default-ssl.conf

sudo nano /etc/apache2/sites-enabled/default-ssl.conf

```
<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin erick9.hi5@gmail.com
                ServerName  zethanath.tk

                ProxyPreserveHost On
                ProxyPass / http://192.168.1.70:8080/index//
                ProxyPassReverse / http://192.168.1.70:8080/index//

                JKMount /* ajp13_worker

                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

                SSL Engine Switch:
                #   Enable/Disable SSL for this virtual host.
                SSLEngine on

                #   A self-signed (snakeoil) certificate can be created by installing
                #   the ssl-cert package. See
                #   /usr/share/doc/apache2/README.Debian.gz for more info.
                #   If both key and certificate are stored in the same file, only the
                #   SSLCertificateFile directive is needed.
                SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
                SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
                Include /etc/letsencrypt/options-ssl-apache.conf

                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>

        </VirtualHost>

        <VirtualHost _default_:443>
                ServerAdmin erick9.hi5@gmail.com
                ServerName  www.zethanath.tk

                ProxyPreserveHost On
                ProxyPass / http://192.168.1.70:8080/index//
                ProxyPassReverse / http://192.168.1.70:8080/index//

                JKMount /* ajp13_worker

                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

                SSLEngine on

                #   A self-signed (snakeoil) certificate can be created by installing
                #   the ssl-cert package. See
                #   /usr/share/doc/apache2/README.Debian.gz for more info.
                #   If both key and certificate are stored in the same file, only the
                #   SSLCertificateFile directive is needed.
                SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
                SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
                Include /etc/letsencrypt/options-ssl-apache.conf

                <FilesMatch "\.(cgi|shtml|phtml|php)$">
                                SSLOptions +StdEnvVars
                </FilesMatch>
                <Directory /usr/lib/cgi-bin>
                                SSLOptions +StdEnvVars
                </Directory>

        </VirtualHost>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

4. Configured my /etc/apache2/sites-enabled/000-default-le-ssl.conf

sudo nano /etc/apache2/sites-enabled/000-default-le-ssl.conf
```

<IfModule mod_ssl.c>
<VirtualHost *:443>

        ServerName zethanath.tk
        ServerAlias www.zethanath.tk servlet.zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/index//
        ProxyPassReverse / http://192.168.1.70:8080/index//

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

</VirtualHost>
</IfModule>
```

5. Configured my /etc/apache2/sites-enabled/000-default.conf

sudo nano /etc/apache2/sites-enabled/000-default.conf

```
<VirtualHost *:80 >
        ServerName  zethanath.tk
        ServerAlias www.zethanath.tk servlet.zethanath.tk

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        #JKMount /* ajp13_worker

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

```

Please note that I have installed libapache2-mod-jk. The content of my /etc/hosts are below.

```
127.0.0.1       localhost
127.0.1.1       erick-ASRock-N68C-GS4-FX
192.168.1.70    zethanath.tk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Here are my question.

1. By typing "http://zethanath.tk" from Firefox, I would get something like below.

[ATTACH=CONFIG]276327[/ATTACH]

Is this correct?

2. By typing "http://www.zethanath.tk" from Firefox, I would get different result.

 [ATTACH=CONFIG]276328[/ATTACH]


Is this correct?


3. By typing "http://servlet.zethanath.tk" from Firefox, I would get the following result.

[ATTACH=CONFIG]276329[/ATTACH]


Is this correct?

4. What I really want to do is to let Apache2 serve my certificate and it should redirect me to TomEE server. I would not let Apache2 serve any content at all, beside the certificate. The rest of the contents should be served through GWT (Google Web tool kit) applications only. I think GWT would expect the setting like below, but I do not know how to do it.

(I cut and pasted the content below from [http://www.gwtproject.org/doc/latest/DevGuideServerCommunication.html#DevGuideServerSide](http://www.gwtproject.org/doc/latest/DevGuideServerCommunication.html#DevGuideServerSide))
[B]
Example[/B]

Let’s assume that the Tomcat server is on a different  host. In this case, there is going to be a problem. Browsers’ Single  Origin Policy (SOP) will prevent connections to ports or machines that  differ from the original URL. The strategy we are going to use to  satisfy the SOP is to configure Apache to proxy a URL to another URL.

Specific directions for configuring Apache and Tomcat for such a proxy setup are at [the Apache website]("http://tomcat.apache.org/tomcat-6.0-doc/proxy-howto.html").  The general idea is to setup Apache to redirect ONLY requests to your  sevlets. That way Apache will serve all the static content, and your  Tomcat server will only be used for service calls. For this example,  assume that:

 
[LIST]
[*]Your Apache server is running on [www.example.com]("http://www.example.com") 
[*]Your Tomcat server is running on servlet.example.com:8080 
[*]Your GWT module has a <rename-to="myapp"> 
[*]You have one RPC servlet, mapped into /myapp/myService 
[/LIST]
The idea is to have Apache proxy requests to the servlet to the other server such that:

[http://www.example.com/MyApp/myapp/myService](http://www.example.com/MyApp/myapp/myService) --> [http://servlet.example.com:8080/MyApp/myapp/myService](http://servlet.example.com:8080/MyApp/myapp/myService)

The following Apache configuration sets up such a rule using a Proxy:

 ProxyPass        /MyApp/myapp/myService  [http://servlet.example.com:8080/MyApp/myapp/myService](http://servlet.example.com:8080/MyApp/myapp/myService)
ProxyPassReverse /MyApp/myapp/myService  [http://servlet.example.com:8080/MyApp/myapp/myService](http://servlet.example.com:8080/MyApp/myapp/myService)
To verify this is working, use a web browser to hit both [http://www.example.com/MyApp/myapp/myService](http://www.example.com/MyApp/myapp/myService) and [http://servlet.example.com:8080/MyApp/myapp/myService](http://servlet.example.com:8080/MyApp/myapp/myService). You should get the same result in both cases (typically a 405: HTTP method GET is not supported by this URL, which is good). If you get something different hitting the second URL, you may have a configuration issue.
 
[LIST]
[*]If you get a 404, there is most likely an error in the left hand side of your URL mapping. 
[*]If you get a “Bad Gateway”, there is most likely an error in the right hand side of your URL mapping. 
[*]If you get a 403 permission error, check the Apache configuration files for <Proxy> tags to see if the permissions are wrong. You may need to add a section like this: 
[/LIST]
 <Proxy \*>
     Order deny,allow
     Allow from all
   </Proxy>

I hope someone can help.

Thank you.

---

### Post by sethanath2 on 2017-08-09
Here is the additional information from my router.

[ATTACH=CONFIG]276332[/ATTACH]

Here is the information from UFW on the server.

sudo ufw status

Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Apache Full                ALLOW       Anywhere                  
20/tcp                     ALLOW       Anywhere                  
21/tcp                     ALLOW       Anywhere                  
990/tcp                    ALLOW       Anywhere                  
40000:50000/tcp            ALLOW       Anywhere                  
Apache Secure              ALLOW       Anywhere                  
8080                       ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Apache Full (v6)           ALLOW       Anywhere (v6)             
20/tcp (v6)                ALLOW       Anywhere (v6)             
21/tcp (v6)                ALLOW       Anywhere (v6)             
990/tcp (v6)               ALLOW       Anywhere (v6)             
40000:50000/tcp (v6)       ALLOW       Anywhere (v6)             
Apache Secure (v6)         ALLOW       Anywhere (v6)             
8080 (v6)                  ALLOW       Anywhere (v6)

---

### Post by sethanath2 on 2017-08-11
Help is greatly appreciated.

Thanks.

---

### Post by sethanath2 on 2017-08-14
I am able to progress a little further. However, I still do not  understand certain things. I pasted my questions at the end of this  posting.

  Here are the steps that I have just done.


1. I reconfigured "000-default-le-ssl.conf". 
 $ sudo nano /etc/apache2/sites-enabled/000-default-le-ssl.conf


```
<IfModule mod_ssl.c>
    <VirtualHost *:443>
        ServerName  zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
    </VirtualHost> 
    <VirtualHost *:443>
        ServerName www.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
    </VirtualHost>
    <VirtualHost *:443>
        ServerName  servlet.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html

        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
    </VirtualHost>
    </IfModule>
```

2. I reconfigured "default-ssl.conf".  
$ sudo nano /etc/apache2/sites-enabled/default-ssl.conf

```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin erick9.hi5@gmail.com
        ServerName  zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html
        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>
</VirtualHost>

<VirtualHost _default_:443>
        ServerAdmin erick9.hi5@gmail.com
        ServerName  www.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html
        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>
</VirtualHost>
<VirtualHost _default_:443>
        ServerAdmin erick9.hi5@gmail.com
        ServerName  servlet.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #DocumentRoot /var/www/html
        JKMount /* ajp13_worker

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on

        SSLCertificateFile /etc/letsencrypt/live/zethanath.tk/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/zethanath.tk/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>
    </VirtualHost>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

3. I reconfigured "000-default.conf". 
$ sudo nano /etc/apache2/sites-enabled/000-default.conf

```
<VirtualHost *:80 >
        ServerName  zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #ServerAdmin erick9.hi5@gmail.com
        #DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        #JKMount /* ajp13_worker

    RewriteEngine on
    RewriteCond %{SERVER_NAME} =zethanath.tk
    RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

    </VirtualHost>

    <VirtualHost *:80 >
        ServerName  www.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #ServerAdmin erick9.hi5@gmail.com
        #DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        #JKMount /* ajp13_worker

        RewriteEngine on
        RewriteCond %{SERVER_NAME} =www.zethanath.tk
        RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

    </VirtualHost>

    <VirtualHost *:80 >
        ServerName  servlet.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / http://192.168.1.70:8080/Index//
        ProxyPassReverse / http://192.168.1.70:8080/Index//

        #ServerAdmin erick9.hi5@gmail.com
        #DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        #JKMount /* ajp13_worker

        RewriteEngine on
        RewriteCond %{SERVER_NAME} =servlet.zethanath.tk
        RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

    </VirtualHost>

    # vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

4. I checked these configuration syntax. 

$ sudo apache2ctl configtest 
Syntax OK

5. I restarted my server.
 
$ sudo systemctl restart apache2

Now, when I typed [http://zethanath.tk](http://zethanath.tk), I would receive the following.

[ATTACH=CONFIG]276395[/ATTACH]

Now, when I typed [http://www.zethanath.tk](http://www.zethanath.tk), I would receive (https) site, which is what I want.

[ATTACH=CONFIG]276396[/ATTACH]

Now, when I typed [http://servlet.zethanath.tk](http://servlet.zethanath.tk), I would also receive (https) site, which is what I want as well.

[ATTACH=CONFIG]276397[/ATTACH]

My questions to you are.

1. What do I have to do to get the (https), when I typed [http://zethanath.tk](http://zethanath.tk) in the browser?
2. From question 1, if it is uncommon to serve [http://zethanath.tk](http://zethanath.tk) as the URL, what I should do to hide it?
3. What is the proper way to serve  (http/https)://servlet.zethanath.tk behind my router only? If I understood correctly, servlet.zethanath.tk should be used as a reference from within Apache server to make redirection to TomEE server only correct? In other words, people outside my router should not be able to access directly correct?

For example, the final configuration from within Apache server should be something like this right? 

        ProxyPreserveHost On
        ProxyPass / [http://servlet.zethanath.tk:8080/NameofApp//](http://servlet.zethanath.tk:8080/NameofApp//)
        ProxyPassReverse / [http://servlet.zethanath.tk:8080/NameofApp//](http://servlet.zethanath.tk:8080/NameofApp//)

Thank you.

---

### Post by sethanath2 on 2017-08-14
> **sethanath2 said:**
> 

1. What do I have to do to get the (https), when I typed [http://zethanath.tk](http://zethanath.tk) in the browser?
  


Regarding the question1, in order to get (https) from [http://zethanath.tk](http://zethanath.tk), I tried the following just now, but it is still does not work. I still get (http) the same way.

$ sudo nano /etc/apache2/sites-enabled/000-default.conf
and 
uncomment all the lines with "JKMount /* ajp13_worker"

<VirtualHost *:80 >
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.

        ServerName  [www.zethanath.tk]("http://www.zethanath.tk")
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / [http://192.168.1.70:8080/Index//](http://192.168.1.70:8080/Index//)
        ProxyPassReverse / [http://192.168.1.70:8080/Index//](http://192.168.1.70:8080/Index//)

        #ServerAdmin [EMAIL="erick9.hi5@gmail.com"]erick9.hi5@gmail.com[/EMAIL]
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
RewriteCond %{SERVER_NAME} =www.zethanath.tk
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>

<VirtualHost *:80 >
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.

        ServerName  servlet.zethanath.tk
        ServerAlias zethanath.tk

        ProxyPreserveHost On
        ProxyPass / [http://192.168.1.70:8080/Index//](http://192.168.1.70:8080/Index//)
        ProxyPassReverse / [http://192.168.1.70:8080/Index//](http://192.168.1.70:8080/Index//)

        #ServerAdmin [EMAIL="erick9.hi5@gmail.com"]erick9.hi5@gmail.com[/EMAIL]
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
RewriteCond %{SERVER_NAME} =servlet.zethanath.tk
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

---

### Post by sethanath2 on 2017-08-14
Do I need to make any change here?

$ sudo nano /etc/hosts

127.0.0.1       localhost
127.0.1.1       erick-ASRock-N68C-GS4-FX
192.168.1.70    [www.zethanath.tk](www.zethanath.tk) servlet.zethanath.tk

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---


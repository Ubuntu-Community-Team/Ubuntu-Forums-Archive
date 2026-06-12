---
title: "Do not get any output from command VBoxManage list runningvms"
date: 2018-03-28
forum: Virtualisation
---

### Post by dirk-lehmann on 2018-03-28
Hello and nice day or night,

maybe my Ubuntu Linux servers are still missconfigured yet:

For example I do not get any output from the command "VBoxManage list runningvms" exectued by user dirk even if dirk (me) is the owner of the process, maybe see:

dirk     22697  2.1  0.3 4903436 105952 ?      Sl   Mär26  78:35  /usr/lib/virtualbox/VirtualBox --comment Webserver --startvm  59e4efc3-4866-4931-a560-92808

Further more on other server a virtual host seems not to use .htaccess even with this vhost.conf:

```
<IfModule mod_fastcgi.c>
  AddHandler php56-fcgi-www .php
  Action php56-fcgi-www /php56-fcgi-www
  Alias /php56-fcgi-www /usr/lib/cgi-bin/php56-fcgi-www
  FastCgiExternalServer /usr/lib/cgi-bin/php56-fcgi-www -socket /run/php/php5.6-fpm.sock -pass-header Authorization

  <Directory "/usr/lib/cgi-bin">
     Require all granted
  </Directory>
</IfModule>

<IfModule mod_fastcgi.c>
   AddHandler php70-fcgi-www .php
   Action php70-fcgi-www /php70-fcgi-www
   Alias /php70-fcgi-www /usr/lib/cgi-bin/php70-fcgi-www
   FastCgiExternalServer /usr/lib/cgi-bin/php70-fcgi-www -socket /run/php/php7.0-fpm.sock -pass-header Authorization

   <Directory "/usr/lib/cgi-bin">
      Require all granted
   </Directory>
</IfModule>

<IfModule mod_fastcgi.c>
   <FilesMatch ".+\.ph(p[345]?|t|tml)$">
      SetHandler php70-fcgi-www
   </FilesMatch>
</IfModule>

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName shop.so-geht-es.org
        ServerAdmin [EMAIL="dirk.lehmann@so-geht-es.org"]dirk.lehmann@so-geht-es.org[/EMAIL]
        DocumentRoot /var/www/shopware
        <Directory /var/www/shopware>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/errors-shop-so-geht-es.log
        CustomLog ${APACHE_LOG_DIR}/access-shop-so-geht-es.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```

As one can see  AllowOverride is set to All, but install-routine of PHP open source Shopware Community Edition seems to ignore this and can not install succesfully or backend is not possile to open after installation! One told me that this has to do with .htaccess.

chmod or rights matrix of /var/www/shopware was 755 and now 777 and even then the .htaccess seems to be ignored by owner www-data.

I was wondering if somebody might explain this to me because I thought with open source everythink gets better for free and is mor reliable and stable than microsoft-based closed source. For me it seems at the moment again that all this PC stuff is tricky and still not a hundred percent simple and reliable as you sit in a car and go for drive if you have driving license.

DL

P.S.: If you would like to know exact version of os and os kernel, feel free to ask. Still doing regular Snapshots with function of the hypervisor of the vm which runs this server because from time to time lack of knowledge and afraid to own support contract because I also do not believe that they might be able to fix such issues quick an easy even if you pay correctly for that. Am I wrong? If so, I have no problem to figure out the solution by my self with trial an error and the help of snapshots.

---

### Post by deadflowr on 2018-03-28
*Thread moved to **Virtualization** *

---


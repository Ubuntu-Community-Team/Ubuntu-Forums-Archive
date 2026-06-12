---
title: "nginx not starting"
date: 2019-05-25
forum: Server Platforms
---

### Post by zak100 on 2019-05-25
Hi,
I was running nginx on ubuntu 18.04 but then I made changes in the "default" by reading information on some websites. Now my nginx is not working. It is apermission denied and pid issue:
                        ```
$ sudo service nginx restart 
```
```


 Job for nginx.service failed becaus the control process exited with error code.

 See "systemctl status nginx.service" and "journalctl -xe" for details.

 
 
 user@lc2530hz:/etc/nginx/sites-enabled$ 

 $ $ systemctl status nginx.service

 &#9679; nginx.service - A high performance web server and a reverse proxy server

    Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: en

    Active: failed (Result: exit-code) since Sat 2019-05-25 13:35:03 CDT; 19min a

      Docs: man:nginx(8)

   Process: 3220 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code

   Process: 3219 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process  
 
 
 May 25 13:35:01 lc2530hz nginx[3220]: nginx: [emerg] bind() to 0.0.0.0:80 failed

 May 25 13:35:01 lc2530hz nginx[3220]: nginx: [emerg] bind() to [::]:80 failed (9

 May 25 13:35:02 lc2530hz nginx[3220]: nginx: [emerg] bind() to 0.0.0.0:80 failed
 May 25 13:35:02 lc2530hz nginx[3220]: nginx: [emerg] bind() to [::]:80 failed (9

 May 25 13:35:02 lc2530hz nginx[3220]: nginx: [emerg] bind() to 0.0.0.0:80 failed

 May 25 13:35:02 lc2530hz nginx[3220]: nginx: [emerg] bind() to [::]:80 failed (9
 May 25 13:35:03 lc2530hz nginx[3220]: nginx: [emerg] still could not bind()

 May 25 13:35:03 lc2530hz systemd[1]: nginx.service: Control process exited, code

 May 25 13:35:03 lc2530hz systemd[1]: nginx.service: Failed with result 'exit-cod

 May 25 13:35:03 lc2530hz systemd[1]: Failed to start A high performance web serv

 lines 1-17/17 (END)

 
```
 
 ==
```


 $  journalctl -xe

```

 ```

-- Defined-By: systemd

 -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

 --  

 -- Unit phpsessionclean.service has finished starting up.

 --  

 -- The start-up result is RESULT.

 May 25 13:42:32 lc2530hz systemd[1]: Starting Message of the Day...

 -- Subject: Unit motd-news.service has begun start-up

 -- Defined-By: systemd

 -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

 --  

 -- Unit motd-news.service has begun starting up.

 May 25 13:42:32 lc2530hz systemd[1]: Started Message of the Day.

 -- Subject: Unit motd-news.service has finished start-up

 -- Defined-By: systemd

 -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

 --  

 -- Unit motd-news.service has finished starting up.

 --  

 -- The start-up result is RESULT.

 May 25 13:42:53 lc2530hz org.gnome.Shell.desktop[1989]: (/usr/lib/firefox/firefo

 May 25 13:42:58 lc2530hz systemd-resolved[782]: Server returned error NXDOMAIN,  

 May 25 13:47:19 lc2530hz /usr/lib/gdm3/gdm-x-session[1855]: (II) event5  - PixAr

 lines 1576-1598/1598 (END)

```

 ==
```


 $  nginx -t

```
```


 nginx: [alert] could not open error log file: open() "/var/log/nginx/error.log" failed (13: Permission denied)

 2019/05/25 14:01:03 [warn] 3564#3564: the "user" directive makes sense only if the master process runs with super-user privileges, ignored in /etc/nginx/nginx.conf:1

 nginx: the configuration file /etc/nginx/nginx.conf syntax is ok

 2019/05/25 14:01:03 [emerg] 3564#3564: open() "/run/nginx.pid" failed (13: Permission denied)

 nginx: configuration file /etc/nginx/nginx.conf test failed
 user@lc2530hz:/etc/nginx/sites-enabled$

```

 ==
```


 /etc/nginx/sites-enabled$ cat default

```
```


 ##

 # You should look at the following URL's in order to grasp a solid understanding

 # of Nginx configuration files in order to fully unleash the power of Nginx.

 # [https://www.nginx.com/resources/wiki/start/](https://www.nginx.com/resources/wiki/start/)

 # [https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/](https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/)

 # [https://wiki.debian.org/Nginx/DirectoryStructure](https://wiki.debian.org/Nginx/DirectoryStructure)

 #

 # In most cases, administrators will remove this file from sites-enabled/ and

 # leave it as reference inside of sites-available where it will continue to be

 # updated by the nginx packaging team.

 #

 # This file will automatically load configuration files provided by other

 # applications, such as Drupal or Wordpress. These applications will be made

 # available underneath a path with that package name, such as /drupal8.

 #

 # Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.

 ##

 
 
 # Default server configuration

 #

 server {
     listen 80 default_server;
     listen [::]:80 default_server;
 
 
     # SSL configuration

     #

     # listen 443 ssl default_server;

     # listen [::]:443 ssl default_server;
     #
     # Note: You should disable gzip for SSL traffic.
     # See: [https://bugs.debian.org/773332](https://bugs.debian.org/773332)

     #

     # Read up on ssl_ciphers to ensure a secure configuration.

     # See: [https://bugs.debian.org/765782](https://bugs.debian.org/765782)

     #
     # Self signed certs generated by the ssl-cert package
     # Don't use them in a production server!
     #

     # include snippets/snakeoil.conf;

 
 
     root /var/www/html;

 
 
     # Add index.php to the list if you are using PHP

     index index.php index.html index.htm index.nginx-debian.html;

 
 
     #server_name_;  

 
 
     location / {

         # First attempt to serve request as file, then
         # as directory, then fall back to displaying a 404.

         try_files $uri $uri/ =404;

     }
 
 
     # pass PHP scripts to FastCGI server

     #

     location ~ \.php$ {

     #    include snippets/fastcgi-php.conf;

     #
     #    # With php-fpm (or other unix sockets):
         fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;

     #    # With php-cgi (or other tcp sockets):

     #    fastcgi_pass 127.0.0.1:9000;

                 fastcgi_index index.php;

                 include fastcgi_params;

     }
 
 
     # deny access to .htaccess files, if Apache's document root

     # concurs with nginx's one

     #

     #location ~ /\.ht {

     #    deny all;

     #}
 }
 
 
 
 
 # Virtual Host configuration for example.com

 #

 # You can move that to a different file under sites-available/ and symlink that

 # to sites-enabled/ to enable it.
 #

 #server {

 #    listen 80;

 #    listen [::]:80;

 #

 #    server_name example.com;
 #
 #    root /var/www/example.com;
 #    index index.html;

 #

 #    location / {

 #        try_files $uri $uri/ =404;

 #    }
 #}
 user@lc2530hz:/etc/nginx/sites-enabled$ 

```



  Some body please guide me.

Zulfi.

---

### Post by LwIh%*7 on 2019-05-28
If you have indeed made changes and want to restore to default configuration follow the following:
```

sudo apt-get purge nginx nginx-common nginx-full

```
Then reinstall nginx by doing:
```

sudo apt-get install nginx

```
That should restore the configuration changes and reset it all.

---

### Post by slickymaster on 2019-05-28
*Thread moved to **Server Platforms**.*

---

### Post by zak100 on 2019-06-05
Hi,
Thanks. This problem is solved now.

Zulfi.

---


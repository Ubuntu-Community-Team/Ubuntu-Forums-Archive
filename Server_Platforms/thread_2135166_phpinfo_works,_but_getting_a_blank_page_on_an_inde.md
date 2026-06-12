---
title: "phpinfo works, but getting a blank page on an index.php"
date: 2013-04-13
forum: Server Platforms
---

### Post by danshea on 2013-04-13
Hello, 

I have a server running Ubuntu with Nginx, php5-fpm and mysql. I created the "phpinfo" file and uploaded it to my server and it works. I can see my phpinfo. however, when I go to run a index.php I get a blank page. Here is my config file. I am running virtual hosts and html files work fine, so I must be missing some kind of setting for the php5. Below is my config file for one of the sites. Does anyone know what I am missing?

Thanks,
Dan
```

# You may add here your
# server {
#    ...
# }
# statements for each of your virtual hosts to this file

##
# You should look at the following URL's in order to grasp a solid understanding
# of Nginx configuration files in order to fully unleash the power of Nginx.
# [http://wiki.nginx.org/Pitfalls](http://wiki.nginx.org/Pitfalls)
# [http://wiki.nginx.org/QuickStart](http://wiki.nginx.org/QuickStart)
# [http://wiki.nginx.org/Configuration](http://wiki.nginx.org/Configuration)
#
# Generally, you will want to move this file somewhere, and start with a clean
# file but keep this around for reference. Or just disable in sites-enabled.
#
# Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
##

server {
        listen 192.168.1.104:80;
        server_name mysite.com;
        access_log /var/log/nginx/mysite.com_access.log;
        root /var/www/mysite;
        index index.php index.html index.htm index.shtml;

location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
                # With php5-fpm:
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
try_files $uri $uri/ /index.php;

        }
}

    # Make site accessible from [http://localhost/](http://localhost/)
    #server_name myservername.com;

    #location / {
        # First attempt to serve request as file, then
        # as directory, then fall back to displaying a 404.
        #try_files $uri $uri/ /index.html;
        # Uncomment to enable naxsi on this location
        # include /etc/nginx/naxsi.rules
    #}

    # Only for nginx-naxsi used with nginx-naxsi-ui : process denied requests
    #location /RequestDenied {
    #    proxy_pass [http://127.0.0.1:8080;](http://127.0.0.1:8080;)    
    #}

    #error_page 404 /404.html;

    # redirect server error pages to the static page /50x.html
    #
    #error_page 500 502 503 504 /50x.html;
    #location = /50x.html {
    #    root /usr/share/nginx/www;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    #    # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
    #
    #    # With php5-cgi alone:
    #    fastcgi_pass 127.0.0.1:9000;
    #    # With php5-fpm:
    #    fastcgi_pass unix:/var/run/php5-fpm.sock;
    #    fastcgi_index index.php;
    #    include fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny all;
    #}
#}


# another virtual host using mix of IP-, name-, and port-based configuration
#
#server {
#    listen 8000;
#    listen somename:8080;
#    server_name somename alias another.alias;
#    root html;
#    index index.html index.htm;
#
#    location / {
#        try_files $uri $uri/ =404;
#    }
#}


# HTTPS server
#
#server {
#    listen 443;
#    server_name localhost;
#
#    root html;
#    index index.html index.htm;
#
#    ssl on;
#    ssl_certificate cert.pem;
#    ssl_certificate_key cert.key;
#
#    ssl_session_timeout 5m;
#
#    ssl_protocols SSLv3 TLSv1;
#    ssl_ciphers ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv3:+EXP;
#    ssl_prefer_server_ciphers on;
#
#    location / {
#        try_files $uri $uri/ =404;
#    }
#}
```

---

### Post by DaveyG on 2013-04-13
Are you using PHP short tags? i.e, ```
<? echo "hello world"; ?>
```

If so, try adding php after <? like so:

```
<?php echo "hello world"; ?>
```

---

### Post by CharlesA on 2013-04-13
What does index.php belong to? I ran into issues when I migrated phpbb3 from Apache to Nginx and all I would get was a blank screen (even with nginx setup correctly).

*shrugs*

---

### Post by danshea on 2013-04-14
I am running phpfox script. I created a "hello world" test page and that works, but not the script /install/index.php  hmmmmmm.

---

### Post by SeijiSensei on 2013-04-16
Have you checked the log files to see what errors PHP has thrown?  Usually if you get a blank page the code is broken before you get to the steps that display output.  I use Apache, so I don't know where nginx stores its logs, but look in the error log and see what errors are reported.

---


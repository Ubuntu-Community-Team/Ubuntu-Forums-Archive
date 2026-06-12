---
title: "Update today (12.04) broke my nginx/php5-fpm setup"
date: 2014-06-30
forum: Server Platforms
---

### Post by Lido on 2014-06-30
I have a few sites running on my server with nginx and php-fpm. I just today ran apt-get update/upgrade and now all but one of my php based sites is giving me the 502 bad gateway error. During the upgrade process I got the question replace/keep/compare the /etc/php5/fpm/pool.d/www.conf, but I kept my original file. The only differences I remember are that some of the options have switched from 666 to 660. This is the set up for one site that broke:
```

    server {
        listen 192.168.1.105:8562;
        server_name mail.mydomain.com:8562;
        access_log /var/www/logs/site1.access.log;
        index index.php index.html index.htm;
        root /var/www/site1/public/;
        error_log  /var/www/logs/nginx.error.log debug_http;

            location ~ \.php$ {
                    # With php5-fpm:
                    fastcgi_pass unix:/var/run/php5-fpm.sock;
                    fastcgi_index index.php;
                    try_files $uri =404;
                    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                    include fastcgi_params;
            }

            # static file 404's aren't logged and expires header is set to maximum age
            location ~* \.(jpg|jpeg|gif|css|png|js|ico|html)$ {
                     try_files $uri =404;
                     access_log off;
                     expires max;
            }
    }
```

---

### Post by Lido on 2014-06-30
It was a permissions issue. In:

```
/etc/php5/fpm/pool.d/www.conf
```

I uncommented these two lines:

```
listen.group = www-data
listen.mode = 0660
```

Then: 
```
sudo service php5-fpm restart
sudo service nginx restart
```

---

### Post by Micky_Gough on 2014-08-14
I had this exact issue. Thanks for posting the update, saved me a lot of debugging. :)

---

### Post by Micky_Gough on 2014-08-14
I had this exact issue. Thanks for posting the update, saved me a lot of debugging. :)

---

### Post by Micky_Gough on 2014-08-14
I had this exact issue. Thanks for posting the update, saved me a lot of debugging. :)

---


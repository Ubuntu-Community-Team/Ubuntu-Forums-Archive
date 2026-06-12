---
title: "nginx conf review"
date: 2010-11-02
forum: Server Platforms
---

### Post by flakzeus on 2010-11-02
I'm in the process of testing several of my WordPress sites. My config works but I'd like someone more familiar with nginx to review the conf and see if I can do anything more efficiently. Keep in mind that I need to use the pretty permalinks. Also, just to note, I'm using the PHP5-FPM package. 

```

server{
        listen *:80;
        server_name server.com www.server.com;

        root /var/www/server.com;
        index index.php
        gzip_static on;

        access_log /var/log/nginx/server.access_log;
        error_log /var/log/nginx/server.error_log;

        client_max_body_size 6M;

        location / {
                try_files $uri $uri/ @wordpress;
        }

        location @wordpress{
                fastcgi_pass  127.0.0.1:9000;
                fastcgi_param SCRIPT_FILENAME $document_root/index.php;
                include /etc/nginx/fastcgi_params;
                fastcgi_param SCRIPT_NAME /index.php;
        }

        location ~ \.php$ {
            try_files $uri @wordpress;
            fastcgi_pass    127.0.0.1:9000;
            fastcgi_index   index.php;
            fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include         fastcgi_params;
        }
}

```

---


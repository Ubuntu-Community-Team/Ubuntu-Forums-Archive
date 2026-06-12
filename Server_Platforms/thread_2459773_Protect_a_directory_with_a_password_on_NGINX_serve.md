---
title: "Protect a directory with a password on NGINX server"
date: 2021-03-25
forum: Server Platforms
---

### Post by paweltech on 2021-03-25
Hello, I created the appo directory in the virtualhost root and added a file in php despite the directive in the virtual host, by logging on to example.com/appo/file.php no user and password are required
```
server {
   listen 80;
   server_name example.com www.example.com;

   # note that these lines are originally from the "location /" block
   root /var/www/example.com/public_html;
   index index.php index.html index.htm;


        access_log /var/log/nginx/example.com.access.log;
        error_log /var/log/nginx/example.com.error.log;

   location / {
      try_files $uri $uri/ =404;
   }
   error_page 404 /404.html;
   error_page 500 502 503 504 /50x.html;
   location = /50x.html {
      root /var/www/example.com/public_html;
   }


        [B]location /appo {
        auth_basic "Restricted";
                auth_basic_user_file /etc/nginx/conf.d/.htpasswd;


}[/B]

   location ~ \.php$ {
      try_files $uri =404;
      fastcgi_pass unix:/var/run/php-fpm/www.sock;
      fastcgi_index index.php;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
      include fastcgi_params;
   }


```

---

### Post by TheFu on 2021-03-25
Check the {} nesting levels for the location /appo. I think you are off 1-2 levels. Indentation doesn't matter and what it shown above has misleading indentation.  I think you are missing a  '}' at the bottom or after the basic-auth stuff - depends on where you want to fix the problem.

I didn't look at other issues, but the "=404;" is completely new to me. Perhaps that is new, but my version of nginx doesn't support it?

I don't do php stuff nor fastcgi stuff, so I cannot help with those. Sorry.

---

### Post by paweltech on 2021-03-26
> **TheFu said:**
> Check the {} nesting levels for the location /appo. I think you are off 1-2 levels. Indentation doesn't matter and what it shown above has misleading indentation.  I think you are missing a  '}' at the bottom or after the basic-auth stuff - depends on where you want to fix the problem.

I didn't look at other issues, but the "=404;" is completely new to me. Perhaps that is new, but my version of nginx doesn't support it?

I don't do php stuff nor fastcgi stuff, so I cannot help with those. Sorry.

i modified, but the problem persists
PS:I point out that I am locally

```

server {
   listen 80;
   server_name example.com www.example.com;

   # note that these lines are originally from the "location /" block
   root /var/www/example.com/public_html;
   index index.php index.html index.htm;


        access_log /var/log/nginx/example.com.access.log;
        error_log /var/log/nginx/example.com.error.log;


        location /appo {
        auth_basic "Restricted";
                auth_basic_user_file /etc/nginx/conf.d/.htpasswd;
                }

   location ~ \.php$ {
      try_files $uri =404;
      fastcgi_pass unix:/var/run/php-fpm/www.sock;
      fastcgi_index index.php;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
      include fastcgi_params;
   }


}


```

---

### Post by TheFu on 2021-03-26
Did you run **sudo nginx -t**?  All good?

Is the htpasswd setup correctly and seeded? [https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/](https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/)
Looks to me like apache's htpasswd tool is necessary.

---


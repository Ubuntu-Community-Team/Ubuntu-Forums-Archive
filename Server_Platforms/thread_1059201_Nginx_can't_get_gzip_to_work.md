---
title: "Nginx: can't get gzip to work"
date: 2009-02-03
forum: Server Platforms
---

### Post by piquadrat on 2009-02-03
Hi,

I have an Nginx server reverse-proxying an apache instance. Nginx is configured to serve static stuff like javascript, css and images. It would be cool if Nginx would gzip the static text files, but it doesn't. My nginx.conf looks like this:

```
user www-data;
worker_processes  1;

error_log  /var/log/nginx/error.log;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
}

http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    access_log  /var/log/nginx/access.log;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;
    tcp_nodelay        on;

    gzip  on;
    gzip_http_version 1.1;
    gzip_vary on;
    gzip_comp_level 6;
    gzip_proxied any;
    gzip_types text/plain text/html text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;
    gzip_buffers 16 8k;
    gzip_disable “MSIE [1-6].(?!.*SV1)”;
    include /etc/nginx/sites-enabled/*;
}
```

And the site-specific stuff:
```
server {
    listen   80;
    server_name  .soemibar.ch;
    client_max_body_size 20000;

    location ^~ /media/ {
        root   /home/www/soemibar;
    }

    location /gallery/plog-content/ {
        root /home/www/soemibar/public_html;
    }

    location / {
        proxy_pass  http://127.0.0.1:8080;
        proxy_redirect  off;
        proxy_set_header    Host        $host;
        proxy_set_header    X-Real-IP   $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /var/www/nginx-default;
    }
}
```

E.g. [http://soemibar.ch/gallery/plog-content/themes/default/gallery.css](http://soemibar.ch/gallery/plog-content/themes/default/gallery.css) should be gzipped, but it isn't. I tried it with the Nginx versions from hardy and intrepid, both deliver the content without gzipping it. What am I doing wrong?

Thanks,
Benjamin

---

### Post by harishcm on 2009-11-25
Nginx was not compiled with the --with-http_gzip_static_module option. Compile it yourself or use a PPA. See the webpage below for details.

[http://wiki.nginx.org/NginxInstall](http://wiki.nginx.org/NginxInstall)

---


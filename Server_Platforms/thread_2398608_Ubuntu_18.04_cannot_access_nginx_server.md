---
title: "Ubuntu 18.04 cannot access nginx server"
date: 2018-08-14
forum: Server Platforms
---

### Post by MarcusL on 2018-08-14
I have a clean install of Ubuntu 18.04 in EC2 for a Laravel project.

I have set up elastic IP, and security groups allowing HTTP, HTTPS through from any source, and SSH and MYSQL from my IP.

I have a virtual host file for my project as follows:

```
server {
    listen 80;
    listen 443 ssl http2;
    server_name .mycalculator.com.au;
    root "/home/ubuntu/mycalculator/public";


    index index.html index.htm index.php;


    charset utf-8;


    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }


    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }


    access_log  off;
    error_log  /var/log/nginx/mycalculator.error.log error;


    sendfile off;


    client_max_body_size 100m;


    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;


        fastcgi_intercept_errors off;
        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;
        fastcgi_connect_timeout 300;
        fastcgi_send_timeout 300;
        fastcgi_read_timeout 300;
    }


    location ~ /\.ht {
        deny all;
    }


}

```

My `nginx error.log` and `access.log` are empty from errors. My `vhost error.log` is also empty. My domain redirects to the elastic IP and I can SSH and connect MySQL Workbench to the DB via SSH.

I can ping the domain in a DOS window and see the correct IP after DNS resolution.

When I run:

```

$ sudo nginx -t 
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

```

```
$ sudo nginx -V
nginx version: nginx/1.14.0 (Ubuntu)
built with OpenSSL 1.1.0g  2 Nov 2017
TLS SNI support enabled
configure arguments: --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-mcUg8N/nginx-1.14.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_geoip_module=dynamic --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module

```

```
$ systemctl status nginx
&#9679; nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
  Drop-In: /etc/systemd/system/nginx.service.d
           &#9492;&#9472;override.conf
   Active: active (running) since Wed 2018-08-15 00:24:08 UTC; 6s ago
     Docs: man:nginx(8)
  Process: 2908 ExecStop=/sbin/start-stop-daemon --quiet --stop --retry QUIT/5 --pidfile /run/nginx.pid (code=exited, status=0/SUCCESS)
  Process: 2923 ExecStartPost=/bin/sleep 0.1 (code=exited, status=0/SUCCESS)
  Process: 2920 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
  Process: 2911 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
 Main PID: 2922 (nginx)
    Tasks: 2 (limit: 1152)
   CGroup: /system.slice/nginx.service
           &#9500;&#9472;2922 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           &#9492;&#9472;2929 nginx: worker process


Aug 15 00:24:08 ip-172-31-6-14 systemd[1]: Stopped A high performance web server and a reverse proxy server.
Aug 15 00:24:08 ip-172-31-6-14 systemd[1]: Starting A high performance web server and a reverse proxy server...
Aug 15 00:24:08 ip-172-31-6-14 systemd[1]: Started A high performance web server and a reverse proxy server.

```


```
$ sudo netstat -plunt | grep nginx
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2922/nginx: master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2922/nginx: master
tcp6       0      0 :::80                   :::*                    LISTEN      2922/nginx: master

```

But when I access the server via browser I get:

```
**This site can&#8217;t be reached**

[COLOR=#646464][FONT=&amp]**mycalculator.com.au** took too long to respond.[/FONT][/COLOR]

[COLOR=#646464][FONT=&amp]ERR_CONNECTION_TIMED_OUT
[/FONT][/COLOR]

```

Any suggestions for where to look next are appreciated!

---

### Post by wildmanne39 on 2018-08-14
*Thread moved to **Server Platforms for a more appropriate fit**.*

---


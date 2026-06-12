---
title: "server 10.04 with nginx 404 errors"
date: 2011-12-21
forum: Server Platforms
---

### Post by hus- on 2011-12-21
What I am trying to do is setup a web server for development running in vmware with the ip address of 192.168.190.128. Nginx is installed and running and I get the "welcome to nginx" page. 

However when I create a subfolder in "var/www" and try to hit "http://192.168.190.128/subfolder" I get a 404 Not found error. The files are owned by www-data, and nginx is running on that account also so I dont think its a permissions issue. 

Here is my nginx configuration. 

```
user www-data;
worker_processes  4;

error_log  /var/log/nginx/error.log;
pid        /var/run/nginx.pid;

events {
    worker_connections  1024;
    # multi_accept on;
}

http {
    include       /etc/nginx/mime.types;

    access_log	/var/log/nginx/access.log;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;
    tcp_nodelay        on;

    gzip  on;
    gzip_disable "MSIE [1-6]\.(?!.*SV1)";

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}
```

Edit: Here is the defualt server config in sites enabled 


```
server {
	listen   80 default;
	server_name  localhost;

	access_log  /var/log/nginx/localhost.access.log;

	location / {
		root   /var/www/;
		index  index.html index.htm index.php;
	}

	location /doc {
		root   /usr/share;
		autoindex on;
		allow 127.0.0.1;
		deny all;
	}

	location /images {
		root   /usr/share;
		autoindex on;
	}

	#error_page  404  /404.html;

	# redirect server error pages to the static page /50x.html
	#
	#error_page   500 502 503 504  /50x.html;
	#location = /50x.html {
	#	root   /var/www/nginx-default;
	#}

	# proxy the PHP scripts to Apache listening on 127.0.0.1:80
	#
	#location ~ \.php$ {
		#proxy_pass   http://127.0.0.1;
	#}

	# pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
	#
	#location ~ \.php$ {
		#fastcgi_pass   127.0.0.1:9000;
		#fastcgi_index  index.php;
		#fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
		#includefastcgi_params;
	#}

	# deny access to .htaccess files, if Apache's document root
	# concurs with nginx's one
	#
	location ~ /\.ht {
		deny  all;
	}
}
```

---


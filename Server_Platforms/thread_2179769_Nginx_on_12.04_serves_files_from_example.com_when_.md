---
title: "Nginx on 12.04 serves files from example.com when accessing sub.example.com"
date: 2013-10-09
forum: Server Platforms
---

### Post by HittingSmoke on 2013-10-09
It's a little more complex than I could fit in the title, sorry. Here's the deal.

I have a site with two subdomains. One of the subdomains is situational and I'd take the vhost down when not in use. I recently noticed that when I take down a vhost for a subdomain, the subdomain will serve files from example.com. This almost resulted in a catastrophic loss of data for the example.com web site.

In my vhost configs sub1.example.com, sub2.example.com, and example.com are all explicity defined in the server_name field. There are no config entries with fallbacks that would (or should?) match one of the subdomain URLs.

I'm running 12.04 with the Nginx package from the repos which is 1.1.19.

Here are my slightly redacted config files:

nginx.conf:
```
user www-data;
worker_processes 4;
pid /var/run/nginx.pid;

events {
	worker_connections 768;
	# multi_accept on;
}

http {

	##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	client_max_body_size 5m;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;
	gzip_disable "msie6";

	gzip_vary on;
	gzip_proxied any;
	gzip_comp_level 6;
	gzip_buffers 16 8k;
	gzip_http_version 1.1;
	gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;

	##
	# nginx-naxsi config
	##
	# Uncomment it if you installed nginx-naxsi
	##

	#include /etc/nginx/naxsi_core.rules;

	##
	# nginx-passenger config
	##
	# Uncomment it if you installed nginx-passenger
	##
	
	#passenger_root /usr;
	#passenger_ruby /usr/bin/ruby;

	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}


#mail {
#	# See sample authentication script at:
#	# http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
# 
#	# auth_http localhost/auth.php;
#	# pop3_capabilities "TOP" "USER";
#	# imap_capabilities "IMAP4rev1" "UIDPLUS";
# 
#	server {
#		listen     localhost:110;
#		protocol   pop3;
#		proxy      on;
#	}
# 
#	server {
#		listen     localhost:143;
#		protocol   imap;
#		proxy      on;
#	}
#}

```

example.com in /etc/nginx/sites-available/:
```
server {
	listen 80;

	root /usr/share/nginx/www/example;
	index index.php index.html index.htm;
	server_name example.com;

	allow all;

	location ~* \.(jpg|jpeg|gif|png|svg|css|js|ico|xml|ttf|otf|eot|woff|mp4|gz|gzip|zip)$ {
		access_log        off;
		log_not_found     off;
		expires           max;	
	}

	location / {
		try_files $uri $uri/ /index.php?$uri&$args;
	}
	location ~ \.php$ {
		try_files $uri =404;
		fastcgi_split_path_info ^(.+\.php)(/.+)$;
		fastcgi_pass unix:/tmp/php5-fpm.sock;
		fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_index index.php;
		include fastcgi_params;
	}
	location /internal_data/ {
		internal;
	}
	location /library/ {
		internal;
	}

	error_page 500 502 503 504 /50x.html;
	location = /50x.html {
		root /usr/share/nginx/www;
	}
}

```

testing.example.com:
```
server {
	root /usr/share/nginx/www/exampletest;
	index index.php index.html index.htm;
	server_name testing.example.com;
	
	auth_basic "Test Environment";
	auth_basic_user_file /usr/share/nginx/.password;

	location / {
		try_files $uri $uri/ /index.php?$uri&$args;
	}
	location ~ \.php$ {
		try_files $uri =404;
		fastcgi_split_path_info ^(.+\.php)(/.+)$;
		fastcgi_pass unix:/tmp/php5-fpm.sock;
		fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_index index.php;
		include fastcgi_params;
	}
	location /internal_data/ {
		internal;
	}
	location /library/ {
		internal;
	}
	error_page 500 502 503 504 /50x.html;
	location = /50x.html {
		root /usr/share/nginx/www;
	}
}

```

maintenance.example.com:
```
server {
	root /usr/share/nginx/www/maintinence;
	index index.html index.php;
	server_name maintinence.example.com;

	location ~* \.(jpg|jpeg|gif|png|svg|css|js|ico|xml|ttf|otf|eot|woff|mp4|gz|gzip|zip)$ {
		access_log        off;
		log_not_found     off;
		expires           max;	
	}
	location ~* /piwik {
		fastcgi_pass unix:/tmp/php5-fpm.sock;
		include fastcgi_params;
		fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_param   SCRIPT_NAME	 $fastcgi_script_name;
	}
	location ~* /phpmyadmin {
		try_files $uri =404;
		fastcgi_pass unix:/tmp/php5-fpm.sock;
		include fastcgi_params;
		fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_param   SCRIPT_NAME	 $fastcgi_script_name;
	}	
	location ~ ^/(apc.php|phpinfo.php|fpm|ping)$ {
		fastcgi_pass unix:/tmp/php5-fpm.sock;
		include fastcgi_params;
		fastcgi_param   SCRIPT_FILENAME $document_root$fastcgi_script_name;
		fastcgi_param   SCRIPT_NAME	 $fastcgi_script_name;		
		auth_basic            "YOU SHALL NOT PASS!";
		auth_basic_user_file  /usr/share/nginx/.password;
	}
	location /nginx {	# Nginx status page
		stub_status on;
		access_log   off;
		auth_basic            "YOU SHALL NOT PASS!";
		auth_basic_user_file  /usr/share/nginx/.password;
	}
	location /index.html {
		auth_basic            "YOU SHALL NOT PASS!";
		auth_basic_user_file  /usr/share/nginx/.password;
	}
	location ~ /\. {
		access_log off;
		log_not_found off; 
		deny all;
	}
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
    }
}

```

I've scoured over my config files over and over again but I can't find anything causing there. These are the only three vhosts that are symlinked from /etc/nginx/sites-enabled/ and there is nothing in the conf.d folder.

Considering Nginx is doing the subdomain routing between vhosts I can't figure out where else this might be caused. My log files have been of zero help. Nginx forums have been unhelpful so far. Anyone have any ideas?

---

### Post by TheFu on 2013-10-10
Isn't there always a default .... so when an IP address is accessed on port 80, a page gets displayed?  Perhaps if you make another vhost and make it the default that isn't on any domain that will be requested?   Just a thought. I dunno.

---

### Post by clearski on 2013-10-10
This is my working vhost config.

I only got a single *default* file in /etc/nginx/sites-available which contains all the server blocks listed below:

```
server {
        listen 80 *default_server*;
        server_name *domain*;
        root /usr/share/nginx/html/*domain*;
        index index.html index.htm;
        location / {
        try_files $uri $uri/ =404;
        }
}


server {
        listen 80;
        server_name* sub1.domain*;
        root /usr/share/nginx/html/*sub1.domain*;
        index index.html index.htm;
        location / {
        try_files $uri $uri/ =404;
        }
}


server {
        listen 80;
        server_name *sub2.domain*;
        root /usr/share/nginx/html/*sub2.domain*;
        index index.html index.htm;
        location / {
        try_files $uri $uri/ =404;
        }
}
```

I've added

```

127.0.0.1       domain
127.0.0.1       sub1.domain
127.0.0.1       sub2.domain

```

to my */etc/hosts* file.

Hope this helps.

---

### Post by CharlesA on 2013-10-10
Have you cleared the browser cache?

I ran into hell trying to get a few subdomains working and having them redirect back to the main domain. That was fixed after clearing the cache on the browser.

Worth a shot, I guess.

---


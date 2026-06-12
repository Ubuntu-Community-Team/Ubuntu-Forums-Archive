---
title: "nginx vhosts not working?"
date: 2021-03-29
forum: Server Platforms
---

### Post by Heeter on 2021-03-29
Hi all,

I currently running Ubuntu20LTS/Nginx1.18/Mysql8/PHP8/Letsencrypt webserver. I have one vhost website functioning properly (nextcloud), trying to add a second vhost (joomla) but it keeps 502 bad gateway when I open in web browser.

I Have done:

Installed joomla files into /var/www/joomla
Created a joomla.conf file in /etc/nginx/sites-available
Linked the joomla.conf to /etc/nginx/sites-enabled.
Successful nginx -t
Restarted nginx and php8-fpm

The joomla.conf has the root set to /var/www/joomla, and has the correct subdomains listed.

The DNS and IP are pointed the correct server, The nextcloud is setup as main domain (domain1.com), and joomla is setup as subdomain (sub.domain1.com)

Don't know if the nginx.conf file corrupted, definitely missing something that I can't see the forest from the trees at this point.

Nginx.conf file:
```

user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

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
	# server_tokens off;

	server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# SSL Settings
	##

	ssl_protocols TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
	ssl_ciphers 'TLS-CHACHA20-POLY1305-SHA256:TLS-AES-256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384';
        #ssl_ciphers 'TLS-CHACHA20-POLY1305-SHA256:TLS-AES-256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA512:DHE-RSA-AES256-GCM-SHA512:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384';
	ssl_ecdh_curve X448:secp521r1:secp384r1:prime256v1;
	ssl_prefer_server_ciphers on;
	
	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;

	# gzip_vary on;
	# gzip_proxied any;
	# gzip_comp_level 6;
	# gzip_buffers 16 8k;
	# gzip_http_version 1.1;
	# gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}

```

Here is my subdomain joomlaconf file:
```

server {
    if ($host = kom.hcctech.ca) {
        return 301 https://$host$request_uri;
    } # managed by Certbot

    listen 80;
    listen [::]:80;
    server_name joomla.domain1.com;
    return 301 https://$host$request_uri;

}

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name joomla.domain1.com;
    ssl_certificate /etc/letsencrypt/live/joomla.domain1.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/joomla.domain1.com/privkey.pem; # managed by Certbot
    ssl_session_tickets off;

    client_max_body_size 1024M;
    fastcgi_buffers 64 4K;

    gzip on;
    gzip_vary on;
    gzip_comp_level 4;
    gzip_min_length 256;
    gzip_proxied expired no-cache no-store private no_last_modified no_etag auth;
    gzip_types application/atom+xml application/javascript application/json application/ld+json application/manifest+json application/rss+xml application/vnd.geo+json application/vnd.ms-fontobject application/x-font-ttf application/x-web-app-manifest+json application/xhtml+xml application/xml font/opentype image/bmp image/svg+xml image/x-icon text/cache-manifest text/css text/plain text/vcard text/vnd.rim.location.xloc text/vtt text/x-component text/x-cross-domain-policy;

    add_header Strict-Transport-Security            "max-age=31536000" always;
    add_header Referrer-Policy                      "no-referrer"   always;
    add_header X-Content-Type-Options               "nosniff"       always;
    add_header X-Download-Options                   "noopen"        always;
    add_header X-Frame-Options                      "SAMEORIGIN"    always;
    add_header X-Permitted-Cross-Domain-Policies    "none"          always;
    add_header X-Robots-Tag                         "none"          always;
    add_header X-XSS-Protection                     "1; mode=block" always;

    fastcgi_hide_header X-Powered-By;

    root /var/www/joomla;

    index index.php index.html index.htm;
    
    location / {
        try_files $uri $uri/ /index.php?$args;
    }

    location ~* /(images|cache|media|logs|tmp)/.*.(php|pl|py|jsp|asp|sh|cgi)$ {
      return 403;
      error_page 403 /403_error.html;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    location ~ /\. { access_log off; log_not_found off; deny all; }

    location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_param        SCRIPT_FILENAME $document_root$fastcgi_script_name;
    fastcgi_pass         unix:/var/run/php8.0-fpm.sock;
    include fastcgi_params;
    }

}

```

Any assistance would be greatly appreciated

---


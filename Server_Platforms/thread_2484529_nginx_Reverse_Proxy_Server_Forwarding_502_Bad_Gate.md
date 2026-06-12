---
title: "nginx Reverse Proxy Server Forwarding 502 Bad Gateway"
date: 2023-03-02
forum: Server Platforms
---

### Post by hans345hamburg on 2023-03-02
[COLOR=#000000][FONT=Arial]Hello,[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I don’t know, if this is the correct forum. I am working in a proxmox environment, setting up a ngnix reverse proxy (192.168.178.103) forwarding requests via https to a nginx backend server (192.168.178.105). On the backend server shellinabox is installed. Request from the internet are encrypted via a Letsentcrypt certificate. For the encryption to the backend server I use a self-signed certificate. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]When I want to open the next-shell.example.com I get an 502 Bad Gateway error[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]On the reverse proxy are the following configs[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]HttpGateway[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Courier New]server {[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]listen 80 default_server;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]listen [::]:80 default_server;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]server_name nextcloud.example.com shellinabox.example.com netdata.example.com px.example.com proxy-shell.example.com next-shell.example.com 192.168.178.103;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]root /var/www;[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New]location ^~ /.well-known/acme-challenge {[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]default_type text/plain;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]root /var/www/letsencrypt;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]}[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]   location / {[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New] return 301 https://$host$request_uri;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]   }[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]}[/FONT][/COLOR]


```

[COLOR=#000000][FONT=Arial]next-shell.example.com[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Courier New]server {[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]listen 443 ssl [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]server_name next-shell.example.com;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]       # SSL configuration[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]       # RSA certificates[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]       ssl_certificate /etc/letsencrypt/next-shell.example.com/rsa/fullchain.pem;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ssl_certificate_key /etc/letsencrypt/next-shell.example.com/rsa/key.pem;[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# ECC certificates[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ssl_certificate /etc/letsencrypt/next-shell.example.com/ecc/fullchain.pem;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_certificate_key /etc/letsencrypt/next-shell.example.com/ecc/key.pem;[/FONT][/COLOR]


[COLOR=#18b2b2][FONT=Courier New]#[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# SSL Configuration[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]#[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Not using TLSv1 will break:[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# Android <= 4.4.40 IE <= 10 IE mobile <=10[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# Removing TLSv1.1 breaks nothing else![/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_protocols TLSv1.2 TLSv1.3;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# SSL ciphers: RSA + ECDSA[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Two certificate types (ECDSA, RSA) are needed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_ciphers 'TLS-CHACHA20-POLY1305-SHA256:TLS-AES-256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-RSA-AES256-GCM-SHA512:DHE-RSA-AES256-GCM-SHA512:ECDHE-RSA-AES256-GCM-SHA384';[/FONT][/COLOR]


[COLOR=#18b2b2][FONT=Courier New]# Diffie-Hellman parameter for DHE ciphersuites, recommended 4096 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_dhparam /etc/nginx/dhparams/dhparams.pem;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Use multiple curves.[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_ecdh_curve secp521r1:secp384r1;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Server should determine the ciphers, not the client[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_prefer_server_ciphers on;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# SSL session handling[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_session_timeout 1d;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ssl_session_cache shared:SSL:50m;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]ssl_session_tickets off;[/FONT][/COLOR]


[COLOR=#18b2b2][FONT=Courier New]# DNS resolver[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]resolver 192.168.178.1;[/FONT][/COLOR]



[COLOR=#18b2b2][FONT=Courier New]#[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# Header configuration[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]#  [/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# HSTS (ngx_http_headers_module is required) In order to be recoginzed by SSL test, there must be an index.hmtl in the server's root[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload;" always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Content-Type-Options "nosniff" always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-XSS-Protection "1; mode=block" always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Robots-Tag none always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Download-Options noopen always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Permitted-Cross-Domain-Policies none always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Referrer-Policy no-referrer always;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]add_header X-Frame-Options "SAMEORIGIN" always;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Disable FLoC[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Permissions-Policy "interest-cohort=()";[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Remove X-Powered-By, which is an information leak[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]fastcgi_hide_header X-Powered-By;[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]location / {[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_set_header Host $host;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_set_header X-Real-IP $remote_addr;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;[/FONT][/COLOR]

[COLOR=#ff0000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_ssl_certificate /etc/selfcerts/stern-example-cert-chain.pem;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_ssl_certificate_key /etc/selfcerts/stern-example-key.pem;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]proxy_ssl_verify off;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]proxy_pass https://192.168.178.105:4200;[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]}[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]}[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]On the backend server there is the following config[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]next-shell.example.com[/FONT][/COLOR]



```
[COLOR=#000000][FONT=Courier New]server {[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]listen 192.168.178.105:4200;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]server_name next-shell.example.com;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]#[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]# Header configuration[/FONT][/COLOR]
[COLOR=#18b2b2][FONT=Courier New]#  [/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# HSTS (ngx_http_headers_module is required) In order to be recoginzed by SSL test, there must be an index.hmtl in the server's root[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Strict-Transport-Security "max-age=63072000; includeSubdomains; preload;" always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Content-Type-Options "nosniff" always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-XSS-Protection "1; mode=block" always;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]add_header X-Robots-Tag none always;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]add_header X-Download-Options noopen always;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]add_header X-Permitted-Cross-Domain-Policies none always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Referrer-Policy no-referrer always;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header X-Frame-Options "SAMEORIGIN" always;[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Disable FLoC[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]add_header Permissions-Policy "interest-cohort=()";[/FONT][/COLOR]

[COLOR=#18b2b2][FONT=Courier New]# Remove X-Powered-By, which is an information leak[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]fastcgi_hide_header X-Powered-By;[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New]ssl_certificate /etc/selfcerts/stern-example-cert-chain.pem;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]ssl_certificate_key /etc/selfcerts/stern-example-key.pem;[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New]location / {[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]rewrite ^/shellinabox/(.*) /$1 break;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]proxy_pass [/FONT][/COLOR][COLOR=#5454ff][FONT=Courier New]http://127.0.0.1:4200;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]proxy_set_header Host $host;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]proxy_set_header X-Real-IP $remote_addr;[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]proxy_read_timeout 350;[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]proxy_connect_timeout 350;[/FONT][/COLOR]


[COLOR=#000000][FONT=Courier New]}[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]}[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]When I try to open the page there is this error in the nginx error log[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Courier New][error] 1103#1103: *1 SSL_do_handshake() failed (SSL: error:0A00010B:SSL routines::wrong version[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]number) while SSL handshaking to upstream, client: 95.116.52.151, server: next-shell.example.com, request: "GET /f[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]avicon.ico HTTP/2.0", upstream: "https://192.168.178.105:4200/favicon.ico", host: "next-shell.example.com"[/FONT][/COLOR]


```
Has anybody an idea?

---

### Post by LHammonds on 2023-03-02
Why do you have both RSA and ECC certificates?  Doesn't the server only utilize the most-recent certificate?

When you created the external Let's Encrypt certificate, I am certain you used a domain name.  But how did you create the internal certificate?  Do you use the internal IP address of the destination server or did you use an internal DNS name?

The "502 Bad Gateway" error is generally a server communication problem.  Make sure your software firewall ports are open on the defined ports you are using (port 4200 for backend, 443 for proxy).  The next thing I'd try is removing the encryption between the proxy and the backend and see if it works which would indicate the issue is in the SSL configuration.

I have not used httpgateway so I cannot recommend anything specific.

LHammonds

---

### Post by TheFu on 2023-03-03
Which versions of Ubuntu and nginx are you using?  
```
$ nginx -v
nginx version: nginx/1.14.0 (Ubuntu)
```

I have a setup for 18.04, but will be moving to 20.04 soon.
I'm not seeing an 'upstream' stanza, which is how I do it.  BTW, I don't do encryption between the reverse-proxy and backend servers.

```
# #########################################
upstream nc-proxy {
        server 172.22.22.33:80;
}
server {
   listen   443 ssl ;
   server_name  nc.example.com;
   include includes/log_format ;

   access_log  /var/log/nginx/nc.access.log;
   error_log  /var/log/nginx/nc.error.log;

   index  index.php index.html ;
   ssl_certificate  /etc/nginx/ssl/nc.example.com/fullchain.pem;
   ssl_certificate_key  /etc/nginx/ssl/nc.example.com/key.pem;
   ssl_trusted_certificate  /etc/nginx/ssl/nc.example.com/cert.pem;

   # Allow and deny all
   include includes/allow_lan_only;

   # Let's Encrypt webroot
   include includes/letsencrypt-webroot;

....
   location / {
       try_files index.html @nc-proxy ;
    }
    location @nc-proxy {
       proxy_set_header  X-Real-IP  $remote_addr;
       proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
       proxy_set_header  Host $host;
       proxy_cache       one;
       proxy_pass http://nc-proxy;
     }
}
```

Let's Encrypt certbot didn't work until I changed to acme.sh for management. Probably my ignorance.  With acme.sh, I use the stand-alone cert request/update.  For about 20 websites - I keep all the certs separate - it takes less than 90 seconds. During that time, nginx is offline.  Only static websites can be updated while nginx is online, IME.

LE requires access from at least 3 different parts of the world before they issue certs.  I had restrictive firewall rules and LE refused to issue any certs.  Because LE moves the IPs around, it wasn't possible to just allow those specific IPs, or at least I wasn't able to easily figure a solution for private servers. In the end, I disable the firewall while the certs are being updated.

---


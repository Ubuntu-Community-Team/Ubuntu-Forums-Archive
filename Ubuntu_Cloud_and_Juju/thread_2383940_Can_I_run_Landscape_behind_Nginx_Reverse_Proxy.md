---
title: "Can I run Landscape behind Nginx Reverse Proxy?"
date: 2018-01-31
forum: Ubuntu Cloud and Juju
---

### Post by mikenjenni on 2018-01-31
Hello,

I have a home network with multiple VM's and one of those being a webserver to host my HTPC running Plex, Plexpy, CP, SABnzbd, etc. This is all accomplished via Nginx reverse proxy w/SSL.

I have successfully installed Landscape on the local network and successfully registered all of my VMs. Everything seems to be working great...on the local network.

But, I'd like to be able to access my Landscape server via my domain name through my Nginx reverse proxy config.

I am wondering if this is possible?

I've tried several different Nginx configurations but it is not working. Do I need to make changes in the Landscape config files or Apache config files on the Landscape server? If so, which ones and how?

Any help would be greatly appreciated!

Here's my Nginx config. I have omitted and changed some of my config for security purposes....but, this is my working Nginx config. Every portion of my Nginx reverse proxy works great...except for the landscape portion which is included below.

I'm trying to access landscape at **[www.mydomain.com/landscape]("http://www.mydomain.com/landscape")**

###########################
server {
listen 80 default_server;
listen [::]:80 default_server;

server_name **[www.domain.com]("http://www.domain.com") domain.com**;
return 301 https://$server_name$request_uri;

}

server {

# SSL configuration

listen 443 ssl http2 default_server;
listen [::]:443 ssl http2 default_server;
server_name **[www.domain.com]("http://www.domain.com")** **domain.com**;
include /etc/nginx/snippets/strong-ssl.conf;
ssl_certificate /etc/letsencrypt/live/**domain.com**/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/**domain.com**/privkey.pem;

# Root location
root /var/www/**domain**;

# Add index.php to the list if you are using PHP
index index.html index.htm index.php index.nginx-debian.html;

# Basic Auth to protect the site
auth_basic "Secure Login";
auth_basic_user_file /etc/nginx/.htpasswd;

# Change the client side error pages (4xx) to prevent some information disclosure
error_page 401 403 404 /404.html;

# First attempt to serve request as file, then as directory,
# then fall back to displaying a 404.

location / {
try_files $uri $uri/ =404;
}

# Deny access to .htaccess files, if Apache's document
# root concurs with nginx's one

location ~ /\.ht {
deny all;
}

ssl_session_timeout 10m;
ssl_session_cache shared:SSL:10m;
ssl_buffer_size 64k;
add_header X-Robots-Tag "noindex, nofollow, noarchive, nosnippet, noodp, notranslate, noimageindex";
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
add_header X-Content-Type-Options "nosniff" always;
add_header X-Frame-Options "SAMEORIGIN" always;

# Let's Encrypt Webroot plugin location -- allow access

location ^~ /.well-known/acme-challenge/ {
auth_basic off;
autoindex on;
}

#Landscape
location /landscape/ {
    auth_basic off;
    proxy_pass **[https://my_landscape_server_ip:443](https://my_landscape_server_ip:443)**/;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_hide_header X-Frame-Options;
}
#########################


Thanks,
Mike

---

### Post by pauldsmyth2 on 2018-11-24
I have exactly the same problem. Disappointing that this thread has been here for 10 months and nobody has bothered to respond.

---


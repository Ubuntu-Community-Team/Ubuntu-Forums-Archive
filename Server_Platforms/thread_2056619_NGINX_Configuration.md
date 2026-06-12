---
title: "NGINX Configuration"
date: 2012-09-11
forum: Server Platforms
---

### Post by Hans83VT on 2012-09-11
Hi there,

I'm trying to get NGINX set up as a reverse proxy server for multiple SSL sites on one IP using SNI.  Requests will come in from 2 different URLs to the reverse proxy server, which will have both SSL certificates installed - it will decrypt the SSL and then push the request to the proper backend server by IP address using regular HTTP.

I have installed Ubuntu Server 12.04 and installed nginx.  I have edited the default /etc/nginx/nginx.conf file to include the following lines:
server {
listen 443;
server_name sub1.site.com;
ssl on;
ssl_certificate /path/to/ssl.pem
ssl_certificate_key /path/to/ssl.pem
location / {
proxy_pass [http://10.0.0.18;](http://10.0.0.18;)
}
}

This is just supposed to forward to one backend server for the moment, but it doesn't work.  When I try to restart nginx, it fails with the message:

nginx: [emerg] invalid number of arguments in "ssl" directive in /etc/nginx/nginx.conf:77

Any thoughts on what I need to do to get it to work?

---


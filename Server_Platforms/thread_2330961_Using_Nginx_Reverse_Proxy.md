---
title: "Using Nginx Reverse Proxy"
date: 2016-07-16
forum: Server Platforms
---

### Post by Souljah on 2016-07-16
Hi,

I have a remote server setup using Ubuntu 16.04. I have installed the latest apache and nginx. I have followed instructions here: [https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-web-server-and-reverse-proxy-for-apache-on-one-ubuntu-16-04-server]("https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-web-server-and-reverse-proxy-for-apache-on-one-ubuntu-16-04-server")

I have a question on this. So my setup is fine. I am able to access "example.com" without any issue. I only use one domain with one IP address. However, I want a specific sub domain, let's say "subdomain.example.com" to be parsed by Nginx and not have it passed onto Apache. How is this configured or can this even be done? Thanks.

---

### Post by TheFu on 2016-07-16
Yes, it can be done.  nginx is a web server after all.

Just setup another "server" file in the /etc/nginx/sites-available/ (subdomain.example.com would be the name I used) without a proxy_pass stanza.  **server_name** setting will be key for the new subdomain. There are plenty of how-to guides for setting up multiple domain support for nginx. About 8 lines in this file should be sufficient if you don't do anything fancy like micro-caching (which is a good idea).  Then when you think everything is good, make a link from that file to the sites-enabled/ directory.

And the default server pattern matching might need to be modified from the example.com config file, so it doesn't slurp the subdomain stuff too. Basically, you are doing name-based virtual servers with nginx.  Pretty easy stuff.  Best of all, nginx doesn't require that stupid .conf file ending apache decided was needed a few years ago.  You are already in the /etc/ directories - it is a conf file clearly.

And if you want to do SSL, just be aware that in the old days, 1 IP address = 1 SSL domain.  In the last few years, that has changed, but it is highly dependent on the client-side browser supporting name-based SSL certs.

I could probably copy/paste a 10 line config if you need it, but using any how-to should be fine.

---


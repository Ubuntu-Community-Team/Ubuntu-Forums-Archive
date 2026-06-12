---
title: "nginx, can't set my local(lan) ip address range"
date: 2014-05-19
forum: Server Platforms
---

### Post by J_Me on 2014-05-19
I need some help in understanding why I get an error when configuring the nginx virtualhost file.
I'm able to:
Set the range for allow users to the defaults which is XXX.XXX.X.0/24 (I can still log on to the web page from an address outside that range within my LAN)
Add specific ip address(s) e.g 'allow XXX.XXX.X.44;' 'allow XXX.XXX.X.75;' and so on.
But not use a range for my actual devices connected to my router, anything other than 0/24 reports an error.
This is a snippet from '/etc/nginx/sites-available/test' file:
```
server {
    root /usr/share/nginx/test;
    server_name myserver.lan;

    location / {
        try_files $uri $uri/ =404;
        allow XXX.XXX.X.0/24;
        allow 127.0.0.1;
        deny all;
    }
 }
```
Thanks

---


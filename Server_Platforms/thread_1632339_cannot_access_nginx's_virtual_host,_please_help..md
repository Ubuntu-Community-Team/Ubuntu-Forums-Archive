---
title: "cannot access nginx's virtual host, please help."
date: 2010-11-27
forum: Server Platforms
---

### Post by feelexit on 2010-11-27
I have windows 7 as host, and used virutalBox created a Virtual Machine, I installed Ubuntu server 10.04 as guest. the network setting is "Bridged Adapter" not "NAT"

I installed Nginx, php and mysql on the Ubuntu server.

on my windows 7, I modify the "host" file, added this line "192.168.1.100 local.www.test.com"

when I test this web site, it goes to the default site, not the virtual host.

here's my nginx config file.

```
server {
    listen 80;
    server_name local.www.test.com;
    access_log /home/feelexit/www/local.www.test.com/log/local.www.test.access$
    error_log /home/feelexit/www/local.www.test.com/log/local.test.error.lo$
    location / {
                root /home/feelexit/www/local.www.test.com/public;
                index index.html index.php;
    }
    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$
    {
		fastcgi_pass 127.0.0.1:9000;
		fastcgi_index index.php;
		include /usr/local/nginx/conf/fastcgi_params;
		fastcgi_param SCRIPT_FILENAME /home/feelexit/www/local.www.test.com/public$fa$
    }
}
```

I pretty sure this config file is fine. is there anything else I have to to make it go to the correct virtual host.

---

### Post by James78 on 2010-11-28
> **feelexit said:**
> on my windows 7, I modify the "host" file, added this line "192.168.1.100 local.www.test.com"
Did you edit the hosts file (/etc/hosts) on Ubuntu and add that entry though?

---


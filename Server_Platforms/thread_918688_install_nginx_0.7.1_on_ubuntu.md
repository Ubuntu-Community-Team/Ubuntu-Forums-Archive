---
title: "install nginx 0.7.1 on ubuntu?"
date: 2008-09-13
forum: Server Platforms
---

### Post by phuongcsa on 2008-09-13
hi all,
pls tell me how to install nginx 0.7.1 on ubuntu.

thanks

---

### Post by windependence on 2008-09-13
How to install Nginx

```
sudo aptitude install nginx
```

How to start Nginx

```
sudo /etc/init.d/nginx start
```

Testing Nginx

[http://localhost/](http://localhost/)


Start and Stop nginx webserver

Following are the commands to start, stop and restart nginx

Start
```
sudo /etc/init.d/nginx start
```

Stop
```
sudo /etc/init.d/nginx stop
```

Restart
```
sudo /etc/init.d/nginx restart
```

No offense but google is a real help with this.

-Tim

---

### Post by phuongcsa on 2008-09-13
thank for your reply,
i am using nginx version 0.5.33 (default package on ubuntu). but now i want to upgrate to v 0.7.1 at [http://wiki.codemongers.com/NginxNews#latest_devel](http://wiki.codemongers.com/NginxNews#latest_devel)

i have a problem with "pair" module when i try instal it on nginx 0.5.33. ([http://brainspl.at/articles/2007/11/09/a-fair-proxy-balancer-for-nginx-and-mongrel](http://brainspl.at/articles/2007/11/09/a-fair-proxy-balancer-for-nginx-and-mongrel))

:(
BR

---

### Post by phuongcsa on 2008-09-14
i found it at [http://blog.elderec.com/2008/07/15/install-nginx-from-source-on-ubuntu-hardy-with-ssl/](http://blog.elderec.com/2008/07/15/install-nginx-from-source-on-ubuntu-hardy-with-ssl/)

:)

---


---
title: "How can I connect my apache server to the world wide web?"
date: 2010-10-20
forum: Server Platforms
---

### Post by malish on 2010-10-20
I have installed LAMP Server and I'm using it but now I want to connect it to the Internet.
I haven't static IP but it isn't problem for me to change my address when I reset my router.
I have already forwarded a port(81) and inserted `listen 81` and a public site that may use it but when I type my IP address it gets Time Out Error.
When I set Listen address and VirtualHost to my public ip address it got this error while starting:
`(99)Cannot assign requested address: make_sock: could not bind to address 109.110.170.200:81`

Thanks a lot.

---

### Post by noway2 on 2010-10-20
You are behind a router and 109.110.170.200 is not likely to be on your LAN domain.  Therefore, you can't bind your server to it directly.  You need to use "port forwarding" to forward the desired port from your public IP connection to your server's IP.  You might also want to look at a service like dyndns (dynamic DNS).

I would suggest that you search either google or even this forum for those terms - you will get lots of information.

Unless there is a reason you can't use it, port 80 would be a better choice than 81 as it is the default.  If you use 81, to access your page it will be necessary to do so like this: [http://your_domain_or_ip:81](http://your_domain_or_ip:81)

---

### Post by wojox on 2010-10-20
[HOWTO: Setup an Apache Web Server For Free ($0)]("http://ubuntuforums.org/showthread.php?t=632841")

---

### Post by malish on 2010-10-20
Thank you for replaying but I already forwarded port 81 ( because I cannot forward port 80) then I inserted `listen 81` and  virtualhost into my apache config after that [http://ip:81/](http://ip:81/)
got timeout
I have googled it but I found nothing.

---

### Post by lethalfang on 2010-10-20
For HTTP/Apache2, did you have the right listening port and the right directory under these two files? Also, the correct permission for the directory (default is /var/www)?

/etc/apache2/ports.conf
/etc/apache2/sites-enabled/000-default

---

### Post by malish on 2010-10-21
I have done that and I can access it from my local network using [http://local-ip:81/](http://local-ip:81/)

---

### Post by malish on 2010-10-21
WORKED!

I was only configured it again and connected a dyndns to it and its working now

Thanks to all

---


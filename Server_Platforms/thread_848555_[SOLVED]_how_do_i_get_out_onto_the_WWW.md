---
title: "[SOLVED] how do i get out onto the WWW?"
date: 2008-07-03
forum: Server Platforms
---

### Post by majikhotline on 2008-07-03
Hello ubuntu country,
I installed Lamp, i created my own simple web site and it only shows up on my local network when i put in the ip address.  how do i get out onto the World Wide Web and do i have to register a domain name?

Thanks for all the help
:guitar:

---

### Post by pytheas22 on 2008-07-03
Is the server behind a proxy?  If so, its IP address probably looks like 10.0.X.X or 192.168.X.X.  If that's the case, you need to configure your proxy server to forward http traffic to your web server in order for the web server to be accessible from the greater Internet.  If it's behind any kind of a firewall (even if it has a non-local IP), you need to open up the http port there as well.

> do i have to register a domain name?


You don't *have* to, but unless you want people to have to enter the IP address of your server (which is probably dynamic, meaning that it will not always be the same) in order to connect, then you probably want a domain name.

---

### Post by majikhotline on 2008-07-03
I have a linksys router and yes the ip address is a 192.168.xxx.xxx number.  so let me get this straight, i have to configure the router to let the web server be seen from the WWW. ok Ill look into that

thanks

---

### Post by pytheas22 on 2008-07-03
Yes, you have to configure the router.  Open up a web browser and type 1921.68.1.1 or 192.168.0.1 and most likely a configuration screen will open (you will need to login first; look on your router for the password).  In the configuration screen, look for an option about port forwarding.  Tell it to forward traffic over port 80 (the http port) to your Ubuntu computer.

---


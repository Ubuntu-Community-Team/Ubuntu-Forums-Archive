---
title: "Ubuntu multiple web servers."
date: 2015-10-21
forum: Ubuntu Cloud and Juju
---

### Post by nadpro on 2015-10-21
I have been trying to get this project working for a long time now and everything I have looked up and tried has had no results.  I Have been trying to run 3 different websites each on their own VM.  I have been able to access them by using port forwarding in pfSense but some connections block port forwarding for security reasons.  currently my setup looks a little like this.  I have a dyndns set up to my internet IP address.

VM1 Apache web server  192.168.1.10  port 80>80               can access by: [www.mysite.net]("http://www.mysite.net")
VM2 OwnCloud Server    192.168.1.11  port 10000>80          can access by: [www.mysite.net:10000/owncoud]("http://www.mysite.net:10000/owncoud")
VM3 Plex Media Server   192.168.1.12  Port 10001>42080     can access by: [www.mysite.net:10001/web](www.mysite.net:10001/web)

I can access my main web server from the internet and my other sites from most internet connections but not all.  I have messed around with reverse proxy's and DNS in my pfSense router with no success.  I would like to access my other sites/servers without using port forwarding such as [www.mysite.net/owncloud]("http://www.mysite.net/owncloud") or [www.owncloud.mysite.net]("http://www.owncloud.mysite.net") or something of that fashion.  I thought I knew how DNS worked but with my lack of success I am beginning to question my knowledge of DNS.  I am not a novice but I am also not an expert, I know I must be missing something I just can't figure out what.

---

### Post by SeijiSensei on 2015-10-21
You can run [proxies on the Apache machine]("https://httpd.apache.org/docs/2.4/mod/mod_proxy.html") to forward connections to the other two hosts.  Each virtual host will need a separate configuration in /etc/apache2/sites-available/.  The two proxied connections will only need a ServerName and the proxy statements in their <VirtualHost> containers.

---


---
title: "Apache Web servers running on VMs"
date: 2015-03-28
forum: Server Platforms
---

### Post by satimis on 2015-03-28
Hi all,

I have installed several websites, each running on its own VMs with following details:

1. They are on name-base and can be evoked on VM browser with /localhose/subdomain(xyz)
(e.g. xyz.domain.com - only with xyz)
2. Each VM is alloted with an internal IP
3. They are running on WordPress
4. Domains are registerd and hosted with Godaddy
5. I'm subscribing 100M/100M up/down Broadband with only ONE fixed/static IP
6. OS of Host and VMs - Ubuntu 14.04

How to configure the servers so that they can be browsed on Internet?  I have been googling a while and found many suggestions.  Following is an example;

Creating Name and IP Based Virtual hosts in debian
[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

Please advise which will be the simple way to configure the websites?  Pointers would be appreciated.

Thanks in advance.

Regards
satimis

---

### Post by nerdtron on 2015-03-28
> 5. I'm subscribing 100M/100M up/down Broadband with only ONE fixed/static IP

This is hard since you are going to use port forwarding of your public IP to the internal IP of the VMs, however you can only use one port forward at a time. So if you port forward port 80 to one VM, you need to choose another port to forward to the other VMs, which is not desirable when you run a webiste where browsers default to port 80 only.

Have you tried exploring virtual hosts on apache so that you can run multiple sites on a single server? this will be easier on your case.

---

### Post by satimis on 2015-03-28
> **nerdtron said:**
> This is hard since you are going to use port forwarding of your public IP to the internal IP of the VMs, however you can only use one port forward at a time. So if you port forward port 80 to one VM, you need to choose another port to forward to the other VMs, which is not desirable when you run a webiste where browsers default to port 80 only.

Have you tried exploring virtual hosts on apache so that you can run multiple sites on a single server? this will be easier on your case.
Hi,

Thanks for your advice.

All websites run on the same VM?

I can do that but there will be more than 25 websites running on ONE VM.

I have VM with 3/4 websites running on it.  They can be evoked with /localhost/xyz /localhost/uvw /localhost/rst etc.  In this case please advise how to configure the web server and the host?  Thanks

Regards
satimis

---

### Post by volkswagner on 2015-03-28
You can have one machine be it a VM or real hardware hosting with [name virtual hosts]("https://help.ubuntu.com/14.04/serverguide/httpd.html").

If you want to have multiple machines hosting sites, you'll need to dedicate one as the reverse proxy server. This will allow
port 80 forward to this server, then any hosts not on this server will need config files (reverse proxy host files) pointing
to the local machines ip for that domain. I made a [little how to]("http://ubuntuforums.org/showthread.php?t=1920715") about this a while back.

As mentioned by SeijiSensei in my how-to, this won't work for ssl sites (port 443). So any sites you want to have ssl enabled should be on the main
server/reverse proxy server.

---

### Post by SeijiSensei on 2015-03-28
> **satimis said:**
> All websites run on the same VM? I can do that but there will be more than 25 websites running on ONE VM.
Most hosting providers support hundreds of sites on a single machine.  Obviously what matters most is the amount of traffic the sites attract.  But unless we're talking about sites servicing hundreds of connections per second, hosting 25 sites on a single machine is not all that demanding.

---

### Post by satimis on 2015-03-28
> **volkswagner said:**
> - snip -

If you want to have multiple machines hosting sites, you'll need to dedicate one as the reverse proxy server. This will allow
port 80 forward to this server, then any hosts not on this server will need config files (reverse proxy host files) pointing
to the local machines ip for that domain. I made a [little how to]("http://ubuntuforums.org/showthread.php?t=1920715") about this a while back.

- snip - 

Hi,

Thanks for your advice and how-to.

Just read;
How TO: Two Web Servers, One IP address = reverse Proxy
[http://ubuntuforums.org/showthread.php?t=1920715](http://ubuntuforums.org/showthread.php?t=1920715)

> 
1. Decide which machine will be the "Main" Server. This will be the server that has port 80 forwarded from your router. This will be your proxy server machine.

I suppose it refers to a VM dedicated for this function - proxy server ?  Port 80/8080 will be forwarded to it on router?

> 
This assumes you have NameVirtualHosts already working on both servers.

I suppose they refer to the web servers running on VMs?  Yes, each VM has its own internal IP assigned on bridge-utils.

On VM (web server)
=====
ls /var/www/html/xyz/```

cgi-bin          wp-blog-header.php    wp-content         wp-mail.php
index.php        wp-comments-post.php  wp-cron.php        wp-settings.php
license.txt      wp-config.php         wp-includes        wp-signup.php
readme.html      wp-config.php.OLD     wp-links-opml.php  wp-trackback.php
wp-activate.php  wp-config.php.ORIG    wp-load.php        xmlrpc.php
wp-admin         wp-config-sample.php  wp-login.php

```
xyz is the subdomain xyz.domain.com hosted on Godaddy server.  On VM browser evoking /localhost/xyz can start the website

Remark:
The website was installed with WordPress.

Please advise which file/files shall I edit and how?

Thanks

Regards
satimis

---

### Post by satimis on 2015-03-28
> **SeijiSensei said:**
> Most hosting providers support hundreds of sites on a single machine.  Obviously what matters most is the amount of traffic the sites attract.  But unless we're talking about sites servicing hundreds of connections per second, hosting 25 sites on a single machine is not all that demanding.
Hi,

Noted and thanks.

I'll clone a VM with Apache web server already running to test it.  I'll install 3/4 websites for this test.

Please advise whether following link is suitable as my guide?

How To Set Up Apache Virtual Hosts on Ubuntu 14.04 LTS
[https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts)

If NO, please shed me some light where to find a how-to.  Thanks

Regards
satimis

---

### Post by SeijiSensei on 2015-03-28
Why not start with the Ubuntu Server Guide: [https://help.ubuntu.com/lts/serverguide/web-servers.html](https://help.ubuntu.com/lts/serverguide/web-servers.html)

---

### Post by TheFu on 2015-03-28
+1 on the reverse proxy. 

You can use it for hundreds of back-end servers or 1. Decide on a service-by-service or website-by-website case.  It can also reverse proxy SSL connections and there are ways to use port 443 for multiple protocols - https, ssh come to mind.  I [use nginx as a reverse proxy and load balancer]("http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers"). It has some amazing capabilities without being as complex as Apache.  It is handy to have static files served by nginx and only get dynamic content from DB driven programs when necessary. nginx can also provide web caching, slow down abusive requests and protect back-end servers from malicious requests. 

Of course, there are probably 50 different solutions for this.

---


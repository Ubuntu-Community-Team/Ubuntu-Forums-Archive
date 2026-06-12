---
title: "You don't have permission to access /owncloud/ on this server."
date: 2019-03-18
forum: Server Platforms
---

### Post by maarten842 on 2019-03-18
Hi there, 

I'am completely new to this and i tried to install owncloud to my Ubuntu server via the following tutorial: 

[https://www.avoiderrors.com/install-owncloud-on-ubuntu-18-04-lts-with-apache2-mariadb-and-php-7-1-support/](https://www.avoiderrors.com/install-owncloud-on-ubuntu-18-04-lts-with-apache2-mariadb-and-php-7-1-support/)

When i am at home at my own internet network it works like a charm. 
But when i am outside of my home internet network and i type 77.163.x.xxx i get the Apche2 Ubunty default page saying "it works"
But when in type 77.163.x.xxx/owncloud it says "you dont have permission to access / owncloud/ on this server. 
 
I dont understand what i'am doing wrong. 

Thanks it advance!

---

### Post by mastablasta on 2019-03-18
first - you should use Nextcloud instead of Owncloud. i went with Owncloud and i regret it now, i plan to move to Nextcloud as soon as i have some time available.

second - you need to have the port open on your firewall to access it from outside. the owncloud likely uses https, and that one uses a different port (443 by default). also make sure your port is forwarded properly on the router: [https://portforward.com/](https://portforward.com/)

eh. it's mostly already explained under the ***Port Forward for External Access*** section on the site you linked.

you can check logs in /var/log to see what is happening on server and why the access was denied. my guess is you skipped a step from the guide or missed something.

---

### Post by TheFu on 2019-03-18
+1 on using Nextcloud instead.  Nextcloud has a crazy vibrant addon community.  Setting up a chat+voice+video chat server is 1 click. I'm not kidding. I've done it.  It is a great way to chat with the kids when I'm travelling.

Those instructions setup a self-signed cert.  Much better to use Let's encrypt free certs for the last few years, though if you aren't an apache guru and php wizard, I'd not allow direct internet access to this webapp.  To setup let's encrypt certs, acme.sh is pretty easy.  I switched from another method just 2 weeks ago. [https://www.howtoforge.com/getting-started-with-acmesh-lets-encrypt-client/](https://www.howtoforge.com/getting-started-with-acmesh-lets-encrypt-client/)

Setup a VPN or always use an ssh tunnel to access your own nextcloud server over the internet.  Both the VPN and ssh access methods should be authenticated using keys, never passwords.  Using password authentication over the internet is a security failure unless using ssh-tunnels or full VPN.

Apache logs are in /var/log/apache/ ... look for issues there.  Google the issue.  
Apache has a configuration checker. When you run that, does the config pass?  
If port 80 works, but port 443/ssl doesn't, then it is either a port forward issue or the SSL setup is wrong.  Also, if you have other websites on that same IP, then things get more complicated quickly.

If that doesn't solve things, best to post the config file files here. Please use code-tags.  I just redid all my Nextcloud server settings recently, so it is fresh in my mind. However, my setup is significantly different from yours since I'm using a reverse proxy and running 20+ other websites on the same public IP.

---


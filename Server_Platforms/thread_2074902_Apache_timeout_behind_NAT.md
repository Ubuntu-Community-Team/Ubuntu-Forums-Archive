---
title: "Apache timeout behind NAT?"
date: 2012-10-22
forum: Server Platforms
---

### Post by billdotson on 2012-10-22
I have Apache 2.2 setup on Ubuntu 12.04 on my local network. I have a dynamic IP, but I have a domain name that is updated with the new IP everytime it changes (no-ip.org). I set up port forwarding on my ISP provided router to forward all HTTP (port 80) and HTTPS (port 443) to my Apache server. 

In my Apache server, any port 80 requests are redirected to port 443 (HTTPS required for the site).

When testing my website on the local network (192.168.x.x) I am able to access it and test it just fine. However, if I type in the public IP (what it is currently) or my no-ip domain  the browser starts to act like it is loading the page. It does that for a few seconds, and then the IP address in the URL area changes from the external IP (or domain name) to the private IP (192.168.x.x) and the HTTPS lock symbol shows up. The browser continues to try to load the page but it times out about a minute or two.

Does anybody have any idea what would be going on here? I wouldn't think I would need to use the ProxyPass or ReverseProxyReset Apache directives... Also, I don't know if my ISP (Charter) is blocking port 80 requests (since I am not paying for their more advanced package perhaps?) but I've heard that can be an issue. If it were my ISP blocking port 80 then why would it resolve the private IP of the VirtualHost at all?

Also, I've seen some things about Apache's "Listen" directive, but I haven't been able to find that directive in any of my config files yet.

Thanks.

---

### Post by shibby4555 on 2012-10-22
Paste your sites-enabled configuration. Also have Charter, port 80 is fine.

---

### Post by volkswagner on 2012-10-23
To see if port 80 is blocked and/or properly forwarded go to [http://canyouseeme.org](http://canyouseeme.org) and check port 80.

It could simply be a nat issue.  To see if it is NAT use a free proxy ([http://hidemyass.com](http://hidemyass.com)) to see if you can access your site, or have a friend outside you lan check your domain/ext ip.

You may be able to change your NAT setting on the router if you find this is the issue.  Or add an entry in /etc/hosts for your domain name and point it to your internal server ip.

---


---
title: "Pointing/Hosting domain name to server at home?"
date: 2010-10-13
forum: Server Platforms
---

### Post by eroomydna on 2010-10-13
I'm using Ubuntu Server (32bit) on a machine at home. I've bought a domain name(s) via Heartinternet.co.uk and my ISP is Bethere.co.uk

I have installed my LAMP Server on my home based server and it's accessible via my static IP address. HTTP is forwarded on my router to my Ubuntu (web)Server.

Now then, in laymen's terms, I want my domain name to resolve to my Ubuntu Server.

I have installed and configured Bind9 to this guide found online:
     [http://goo.gl/M3Pk](http://goo.gl/M3Pk)
I understand that I need to do this in order to 'host' the domain name. Or alternatively, if my presumptions are correct, I could leave the domain name with the registrar and use their DNS config panel to add an A record to point at my webserver (static IP address)???

If I forward port 53 (default for DNS) to my server (after setting up bind9 correctly) and within my domain name hosting options change the nameserver settings to point at my static ip address then would this be enough to host my domain from my home network?

I feel I nearly have a whole picture but...not quite.

There's a multitude of vague guides on the internet (vague or I'm not reading them properly!)

Any assistance would be awesome.

Andrew

---

### Post by cj13579 on 2010-10-13
The easiest thing to do is edit the DNS record from your domains host's control-panel/website/thing to point to your IP. Any requests on any ports for that host will then be forwarded to your IP. Then it's just a matter or you forwarding the ports that you want to open on to your box :)

---

### Post by ed12348 on 2010-10-13
I run my own web server from home, it is reasonably simple to do if you know what you have to do.

It boils down to a handful of steps

1. Check if your IP is Static or Dynamic
2. If your IP is dynamic use a dynamic DNS service
3. Change the DNS records of your domain name to point to your Static IP or the address provided by the dynamic DNS service
4. Forward port 80 on your home router to your server's IP address
5. Enjoy :D

If you are on a cable internet connection your IP is usually static, if your connection is served over a standard telephone line it is usually dynamic. Static IP's are easier to work with, some Internet Service Providers will provide a Static IP on request, however they usually charge an annual or monthly fee for this.

If a static IP is too expensive or not an option then you can use a dynamic DNS service such as the one from DynDNS.com, these are usually free.

You then need to change the DNS records with the domain name host you use. Most good domain name hosts will provide good help files explaining how to change the DNS settings with them.

If your server plug directly into the modem then you don't need to change anything else. 

However if you have a wi-fi router in your home or if you use a LAN router you have to open the network config on your server and take down its internal IP address (usually along the lines of 192.168.x.xx).

Then google "Port Forwarding" and the model or name of your router. Then follow the instructions you find to forward port 80 to the IP address of your server.

Then you are all done.

If you have to set
Hope this has been of some help.

---


---
title: "Configuration of Router to allow access from other computers on network"
date: 2007-06-21
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-06-21
Here is my network setup: 

1. DD-WRT router with firewall on
2. 1 Ubuntu Box
3. 1 Windows XP Box

My ubuntu box has apache installed, but it is only listening to localhost for requests.  Next, I would like to open it up so that I can serve requests from my windows box.  I would also like internet access from both computers.

Will my router filter out hackers or do I need to do something special with port fowarding or apache setup?  I am worried that if I listen to more than localhost, I am opening up my box to the whole world.  Is this true?  I really only want to open it up to just computers on my own network.

In a month or so, I would like to open up the ubuntu box to the the internet so I can start hosting picture galleries and doing remote administration.  

What kind of router configuration and apache configuration do I need to do?  Will I be vulnerable if I listen to more than localhost?

I followed the Listen directive suggestions on 
[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)
in order to protect it from malicious visitors.

Can someone please straighten me out and point me in the right direction? I am really confused with apache, port forwarding and all.

---

### Post by turinglabs on 2007-06-21
If you want to serve web traffic over the network, then yes, you need to listen on whatever interface is connected to the rest of your network, usually eth0. For most servers, there is only one active network interface apart from lo (the loopback or localhost), so the choice is easy.

Unless your router/firewall is fowarding web requests from the internet into your web server, then no, listening on other than localhost will not allow direct internet traffic in. There is a concept of 'routable' and 'non-routable' IP addresses (apologies if you know this aleady!). Routable IP's can be seen on the Internet, non-routable cannot. There are ranges of non-routable or private IP addresses, the most commonly seen in home LAN's look like 192.168.x.x. If you are using non-routable IP's for your LAN (as you should), then no one on the Internet will be able to see your servers, unless you are doing port-forwarding on your router. 

If you do enable port-forwarding on your router, TCP port 80 requests from the Internet will be sent in to your Ubuntu/Apache box. You would have to let the world at-large know what IP address to use, in this case you create a DNS entry that translates your web server's hostname to your router's Internet IP address. DynDNS (dyndns.com) is a free and easy way to do this, or if you have your own domain you can usually setup DNS through your domain registrar.

There can be more complications if your router's Internet IP is dynamic (typical on home DSL or cable lines), or your ISP blocks inbound port 80, but this should get you started.

---


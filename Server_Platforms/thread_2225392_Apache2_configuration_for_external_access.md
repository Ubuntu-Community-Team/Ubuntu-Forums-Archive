---
title: "Apache2 configuration for external access"
date: 2014-05-21
forum: Server Platforms
---

### Post by Toxic64 on 2014-05-21
Hello All, 

I'm having a problem here I can't seem to find a solution to.

I set up an apache virtualhost on ubuntu 12.04.3 for a website on a network. 
I set up HTTP and HTTPS fotr the website and both are working fine from the inside of the network.
then I have created a nat on my router for port 443 to 25443 and there begins the problem.
the website is not accessible from the outside of the network. it returns a connection timeout...

I have followed many guides on such problems but didn't seem to find anything working.

from the inside I have access working on 

[http://ip](http://ip)
[https://ip](https://ip)

[http://dnsname](http://dnsname)
[https://dnsname](https://dnsname)

AND 

[https://public](https://public) ip:25443

please can somebody help?

thanks in advance.

---

### Post by thufirhawat2 on 2014-05-21
Hey!

If you open the available sites configuration (sudo nano /etc/apache2/sites-available/default-ssl.conf) do you have a line that says 

"ServerName publicDNS/IP:25443" 

without the quotations? I have never added that line by IP before, I use DDNS to host my site, so I am not sure it would work with just the public IP there. I had to add that line to host my SSL site on a port other than 443 though, even though the server listens on 443 locally. Hope that helps!

---

### Post by Toxic64 on 2014-05-22
Hi, 

I didn't have this line though I had a line pointing to localIP:443

I added the line but no luck with that. Still doesn't work...

---

### Post by thufirhawat2 on 2014-05-22
Hmm, so from a computer that is on the same LAN as your server, you can go to [https://publicip:25443](https://publicip:25443) and you hit your site, but when you are on a PC that is not on the same LAN, [https://publicip:25443](https://publicip:25443) does not bring up your site, correct? 

What does your network topography look like, do you have a modem from your ISP with a router connected to it? Is the ISP's modem also a router? If you do a trace route, (tracert [www.google.com]("http://www.google.com") on a windows PC in a DOS prompt or if on a Linux machine sudo apt-get install traceroute and then do a traceroute [www.google.com]("http://www.google.com")) does the trace show two local IPs before hitting the first public IP? So the first IP it shows should be your router, probably 192.168.1.1 or something like that, but is the second IP in the list also a local IP like 10.0.0.1, or 192.168.0.1 or anything like that? The machine that is on your LAN may be being directed to your server by the router without ever having to leave the LAN, but a machine on the outside has to go through that modem first, and if it is also a router with a built in firewall, you would either need to forward the appropriate ports through it to your router, or bridge it to the router.

---

### Post by Toxic64 on 2014-05-22
Well I guess it' really an apache problem.

I have installed webmin on this server too which uses it's own miniweb server and it works without problem through [https://publicIP:10000](https://publicIP:10000)
so only the apache sites don't seem to accept external requests.

We've already had all the needed ports nated. there is a firewall on the router though but I don't see xhy it would allow webmin miniwebserver through and not apache.

I did a traceroute. first IP is indeed the router which is expected second IP is not a local IP

---

### Post by thufirhawat2 on 2014-05-23
Hmm, so from your LAN, you said you can in fact do [https://publicIP:25443](https://publicIP:25443) and hit your site, but what about http, does it also work locally using the public IP? I am kind of running out of ideas, you might post your apache2.conf, default-ssl.conf, and 000-default.conf. If it is not network related, it would just about have to be in one of those config files, maybe myself or someone else could see something in there that lights a bulb.

---


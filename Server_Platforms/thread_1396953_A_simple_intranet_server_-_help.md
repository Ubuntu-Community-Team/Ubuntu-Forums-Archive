---
title: "A simple intranet server - help"
date: 2010-02-02
forum: Server Platforms
---

### Post by leegold on 2010-02-02
Hi,

Please if you could just orient me I will do the reading. I want to set up what I assume is called an intranet server. Initially it'll just serve html web pages to users on my local Ethernet. BTW, right now users get their ip addresses from a router - 192.168.xxx.xxx - "private" IP's. This router is then connected to a modem which then connects to the internet, so there's the usual ip masquerade... I assume I'll install Ubuntu server on a dedicated PC connected to the local Ethernet. 

My question is I want to insure that no one from the "outside" will ever be able to connect to the server, it's only for locals. Also locals should be able to connect to the internet and also should be able to connect to this local server if they want. What is the simplest way to implement? Are my simple assumptions correct? 

Thank you.

Lee G.

---

### Post by Rich78 on 2010-02-02
I would look to setup Apache and then block all unwanted incoming traffic on your router assuming it has a decent firewall.

---

### Post by munky99999 on 2010-02-02
Yep you just set it up like any ole webserver.

[https://help.ubuntu.com/9.10/serverguide/C/httpd.html](https://help.ubuntu.com/9.10/serverguide/C/httpd.html)

Then block using iptables everything except local traffic. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

If you are interested. You could setup the dns provider to provide an A host to Webserver.lan. So basically anyone on your network who might go to your webserver doesnt need to know the ip; just the webaddress of [http://webserver.lan](http://webserver.lan)

So you dont setup dns on the webserver necessarily; but you goto whatever your current provider is; which is likely 1 hop from the modem.

---

### Post by tlsarles on 2010-02-02
Get a Ubuntu Server Disc, and install it. Durring the install it asks " Why did you install this? " and it will give you some options. Just check the box next to "LAMP Server" or "web server" or whatever they call it.

As far as security goes... Given that you using a 192.168.x.x address scheme, you are on a NAT'ed network, and aren't really subjected to Internet traffic. In fact, you would have to do additional configuration on your router to be able to hit your web server from the internet.

If your paranoid tho, you can set an IP range as allowed hosts in the Apache config. The IPTables suggestion would provide even greater security in this aspect if you want to block all non local traffic to the box, and not just web traffic.

DNS is a good idea if you feel like screwing with it too, but I would say that is outside the scope of your immediate question. Cool none the less...

BTW, once installed your website's root directory will default to /var/www/

---

### Post by FuturePilot on 2010-02-02
You shouldn't have to do anything extra to block external traffic seeing as you're behind a router. Unless you forward ports to the server, no one from outside can access it.

---

### Post by tr333 on 2010-02-03
> **munky99999 said:**
> 
Then block using iptables everything except local traffic. 

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


I would suggest using [ufw](https://help.ubuntu.com/9.10/serverguide/C/firewall.html) instead of iptables.  It's a bit easier to configure for applications.

---

### Post by quietas on 2010-02-03
Right off the bat I would recomend keeping it simple. Am I correct to assume you are behind some sort of firewall/router? If that is a yes, and you are using private 192.168.x.x IP's, then you machine is perfectly fine unless you specifically setup some sort of port forwarding manually.

All this talk of firewalls and such is pointless if your machine is already behind a firewall unless you need to protect the linux server from the people inside the firewall.

As for the intranet portion, your terminology is correct. A simple Wordpress blog is a good way to share info, or a multi user Wordpress MU works great if you need multiple blog sites on it.

---

### Post by R.Bucky on 2010-02-03
Yup, unless DNS is configured to point to your static ip AND you have port 80 forwarded to that box, go for a LAMP stack install and don't worry about it. Assuming that you are operating a MS Server variant, configure DNS and you are off and running!

---


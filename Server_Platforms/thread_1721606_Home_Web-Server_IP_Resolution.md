---
title: "Home Web-Server IP Resolution"
date: 2011-04-04
forum: Server Platforms
---

### Post by rowzy1984 on 2011-04-04
Hello good people of the Ubuntu community.

I am trying to setup a home server to host a domain I purchased through GoDaddy. 
Lets call that domain [www.xyz.com](www.xyz.com) for now, and my IP address 123.456.789.101

I have setup apache2, mysql, php5, even webmin and phpmyadmin. They all work correctly on my local network (if I access from another machine via the local IP 192.168.0.110) It all runs fine, and I can run all the pages I need to run. 

My problem is this: When I type in the server's IP address on the WAN as it is above (123.456.789.101), I get any variation of "Cannot display the page". 

I also ran into an error when configuring a static IP for the server, so it is currently dynamic. My ISP is also telling me that I have a static IP as well. 

I've tried searching/googling with many conflicting results, I tried to use 5 of them on completely clean installs of  Apache, mysql, php with no luck.

I've used the following 3 pages as a guide, just intending to get up and running. 

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

[http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/)
 
[http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/](http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/)

I followed the guides very closely, I wasn't rushing. I should mention that I am more in this to learn how than for the end result of running a web site from my home. 

I am certainly willing to provide any of the contents of the configuration files/code necessary. And I apologize in advance for any noobism which may be cast upon this post. 

Also, thank you for your time and attention. 
It is much appreciated.

Matt

---

### Post by Kljuka on 2011-04-04
You first need to figure out if your IP address is static. Google for: what is my ip address to see what is really your IP.
Try accessing webpage from outside (computer that is not part of your network. Routing traffic to your internet IP address from inside might be a challenge for your router). Use Web proxy server (go to [http://www.cool-proxy.net/index.php?action=web-proxy-list&sort=working_average&sort-type=desc](http://www.cool-proxy.net/index.php?action=web-proxy-list&sort=working_average&sort-type=desc) and choose one of them and try accessing your IP (or your site)).

If you use Domain name (and not ip) for accessing your webserver, you'll also need to configure DNS records (which GoDaddy offers for free) (A record to be exact).
Hope this helps for the start

---

### Post by arrrghhh on 2011-04-04
Well for one I would make the server a static IP - it'll be easier for the next step.

Next step being port forwarding - you probably don't have UFW enabled, so by default it'll allow whatever traffic on your LAN.  However, you probably also have a router with a hardware firewall - this does not allow traffic by default, and you need open ports on it directed to the server - this is why a static IP is important.  The router needs to know what IP address on your LAN it should forward the port for (this is NAT).  You don't want the server IP to change, or else you'll have to change the port forward entry in your router.

Each router is different, see portforward.com if you need help sorting out how to forward the ports on your router.

---

### Post by rowzy1984 on 2011-04-04
Hi Kljuka and Arrrghhh,

I forgot to mention I do have my port 80 forwarded to the server's local IP. I tried to access via the domain name both on and off my network (tried at work). My IP (via [www.whatismyip.com](www.whatismyip.com)) is as I mentioned (123.456.789.101 - changed for security purposes). I just tried via the proxy server to get at it with my IP and it works!! Kudos Klujka for that one. 

As for DNS records, I have tried to configure them with the A record pointing at my IP, but I feel quite lost with respect to nameservers. I have configured the nameservers of my ISP to my DNS records, but again, I'm pretty under-confident there.

I am going to work on configuring the static IP on the server itself right now.

Thanks again to both of you, I am amazed at the response time.

Matt

---

### Post by fela on 2011-04-04
Configuring a static local IP for your server is a simple matter of going into your router's config, going to the equivalent of 'local network', selecting your server, and clicking the option 'static' (or whatever it might be laid out as).

As for A records/DNS, it might all seem a little confusing at first, but it boils down to just this:

1. Get a domain name.
2. Add an A record to it, pointing to your **public IP**.

That's it.

edit: well obviously you don't even need the domain name if you just want to access it via the IP, in which case you'd enter your public IP address in your web browser. If you're having problems, I'd do this first to eliminate possible misconfigurations.

---

### Post by rowzy1984 on 2011-04-04
Thanks fela,

   I have this all set. What nameservers should be listed with GoDaddy? Their NS or my ISP's or other?

Thank you very much,

Matt

---

### Post by fela on 2011-04-04
> **rowzy1984 said:**
> Thanks fela,

   I have this all set. What nameservers should be listed with GoDaddy? Their NS or my ISP's or other?

Thank you very much,

Matt

I would have thought you should just use their default name server. When I setup my domains using fasthosts.co.uk, I never had to specify name servers (I don't even think I had/have the option!)

---

### Post by rowzy1984 on 2011-04-04
hmmm alright, I will change back to their default NS's and allow it to propagate.

Thanks for the help fela.

Cheers!

Matt

---

### Post by fela on 2011-04-04
> **rowzy1984 said:**
> hmmm alright, I will change back to their default NS's and allow it to propagate.

Thanks for the help fela.

Cheers!

Matt

No problem. Propagation should be instant, at least it is on my provider, don't know about goDaddy.

---

### Post by rowzy1984 on 2011-04-05
Good news,

Woke up to this morning to find the domain name resolving correctly. 

Thanks everyone again for your help. 

Talk soon,

Matt

---

### Post by fela on 2011-04-05
Glad it worked out.

---


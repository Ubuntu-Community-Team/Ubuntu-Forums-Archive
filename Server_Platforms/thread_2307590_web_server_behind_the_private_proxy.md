---
title: "web server behind the private proxy"
date: 2015-12-26
forum: Server Platforms
---

### Post by iamsurf3r on 2015-12-26
Hi,

I'm new here and also relatively new to web administration. I am hosting my web server at home. ISP gives me dynamic IP, so I use DYN DNS service to get free domain (for example like "mysite.ddns.net").
I've found that my ISP shares some of my personal data that you can get with REVERSE DNS lookup. So I've decided to run my home web server behind private proxy that I bought from proxy provider. The proxy is really fast. Is it a good idea?

Anyway, I still can't find the way to configure Apache. Could you, please, help or point me to the right topic?
I believe that the scheme should be like: Apache -> ProxyIP:port -> Internet (for outgoing connections) and Internet -> mysite.ddns.net -> ProxyIP:port -> Apache. Is it correct?
The proxy I got supports both user/pass and ip authentication.

So, basically what I want is that if someone enters my domain name will see my proxy ip and not my real home ip where the server runs.

Currently I'm digging in Apache's mod_proxy module. Already tried many attempts, but can't understand how I can get it.

Thanks for any tips!

---

### Post by TheFu on 2015-12-26
I don't think commercial privacy proxy providers allow inbound connections.
The mod_proxy in apache is for a reverse proxy, so if you don't run that outside your network, it won't do you any good to enhance any perceived privacy.  [http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers) might be helpful.

If you want to run a service and not make it available to the world, perhaps using a VPN is really what you want?  There are other non-standard, wholly encrypted networks too. .onion addresses are for tor-based services. That might be what you want too?

---

### Post by matt_symes on 2015-12-26
Thread moved to **Server Platforms**

You may get better help for your query here.

---

### Post by iamsurf3r on 2015-12-26
Thanks for an explanation, good article and moving thread to other location!
I decided to leave the idea of hiding home web server's ip behind proxy (though I heard it possible with nginx) and looking forward to keep better security, like redirecting unsafe requests, bad configuration, overflows and etc, what could be even more important.

I just wanted to try hosting website at home during development and feel safe for everything that could happen in that case, when you use your home IP for such things )))
At least I learned a lot of new things from that. The idea to hide IP behind proxy came after this short test [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) , when I saw that my ISP provides some personal data ([FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=2][COLOR=#000060]DNS machine name)[/COLOR][/SIZE][/FONT], when you make Reverse DNS lookup.

---

### Post by TheFu on 2015-12-26
I wouldn't worry too much based on GRC talks. Most things that are shown are just part of networking and not a big deal. The "stealth" stuff really isn't all that useful for people with a proper firewall who don't open any ports.  If you open any ports, then it is expected you understand the risks and will mitigate to the level needed for those risks.

---

### Post by MAFoElffen on 2015-12-27
There is also another strategey that we practiced in CISCO and server admin courses... 
> 
Problem:
You need to keep a web server secure and available from the Internet and from an internal private network.
Solution
This solution protects and provides access to the web server by:
Installing the web server on a DMZ (demilitarized zone) network separate from your internal network that exposes the web server to the Internet and the internal network. Connecting the DMZ network to subnetted or physically a different NID so that the DMZ network is separated from the internal network.
Using your firewall and routing tables to:
- Creating a destination NAT (DNAT) security policy that includes UTM protection and that allows users on the Internet to access the web server.
- Creating a route mode security policy that allows users on the internal network to access the web server.

Simplistically using what you have to do rule based port forwarding... where as a proxy (as an added server service) located in the DMZ is at a different level and provides "different" detail in what it does and can do. Personally, I think using a proxy is a more elegant solution.

---

### Post by TheFu on 2015-12-28
There are caching services that will help with this too - cloudflare, for example. At least I think they will.

Been running a reverse proxy for over a decade, but only to perform load balancing and remove bogus requests. Never intended to "hide" anything, though client machines don't need to know if I'm using Perl + Dancer, or Catalyst or RoR or straight php ... thanks to the proxy doing outbound filtering.

It is worth differentiating between a "proxy" and a "reverse proxy". IMHO.  For most people, a proxy is something their company has to limit web traffic, not the other sort that we are discussing here.

---


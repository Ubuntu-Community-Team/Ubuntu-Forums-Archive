---
title: "Connection timeout apache"
date: 2014-07-29
forum: Server Platforms
---

### Post by noah10 on 2014-07-29
I can access my website  via [www.noahpcfreak.info](www.noahpcfreak.info) , internal & external ip... but no one else can.
When i try and open website through a proxy always says connection timeout. Friends say they cant connect to it also. Where do i even begin?

On intodns.com/noahpcfreak.info everything seems alright. 

I ping my site, get a response.
nslookup:

server: google-public-dns-a.google.com
address: 8.8.8.8

non-authoritative answer:
name: noahpcfreak.info
[noparse]address: 72:198:xxx:xx[/noparse]


Can any of you guys connect to it? ping it and tell me results? and or look at intodns and tell me if you you the problem.

---

### Post by CharlesA on 2014-07-29
You'd need to provide more info.

---

### Post by noah10 on 2014-07-29
> **CharlesA said:**
> You'd need to provide more info.
Tell me what you need to know.

---

### Post by CharlesA on 2014-07-29
How is the machine set up. Is it behind a router?

Are you able to access it from outside your local network - cell phone, etc?

---

### Post by lisati on 2014-07-30
The first thing I'd check is that port forwarding on your router is set to point to the correct machine, i.e. your server. 

When I was running a server, I found it helpful to set a static/reserved IP address for my server on my router's control panel, and then set port forwarding on my router to redirect incoming requests to the server's internal IP address.

---

### Post by Doug S on 2014-07-30
> **noah10 said:**
> Can any of you guys connect to it? ping it and tell me results? and or look at intodns and tell me if you you the problem.I can not connect. I get no reply for ping. I did not look at intodns, as I am not sure what is wanted there.

---

### Post by noah10 on 2014-07-30
> **lisati said:**
> Is port forwarding on your router set up? Is your server on a static IP address on your LAN?
Port Forwarded yes, static no BUT should work for the time being. 

are you able to connect to [http://noahpcfreak.homeserver.com](http://noahpcfreak.homeserver.com) by change?

Odly enough my buddy was able to connect and see a page from the webserver from that link. just not my domain.

---

### Post by Doug S on 2014-07-30
> **noah10 said:**
> are you able to connect to [http://noahpcfreak.homeserver.com](http://noahpcfreak.homeserver.com) by change?No. (it resolves to the same address, so I didn't even try to ping)

---

### Post by noah10 on 2014-07-30
> **Doug S said:**
> No. (it resolves to the same address, so I didn't even try to ping)
Oh. Well this is all again just for fun. Been at this for 2 days now with no prior knowledge of web hosting. 
However i am stuck right now. You have any suggestions for troubleshooting? 
Or try to explain how i can connect to the site via noahpcfreak.info, internal ip, and external but no one else can?

Ive been paying attention to my dns options, and looking at intodns.com  as suggestion from reading online. From what i can tell things look alright. On my end my nameservers resolve to my ip. Just no one can view the site.

The only thing i can think of is being my firewall, or ports not working. But i forwarded ports already, disabled firewall. I dont get it.

---

### Post by noah10 on 2014-07-30
> **CharlesA said:**
> How is the machine set up. Is it behind a router?

Are you able to access it from outside your local network - cell phone, etc?
Behind a router yes, in hyper v vm to be exact. 
Not able to access the site externally (outside network). 

earlier today my friend was able to connect via a different domain that i had setup for my whs server. So i know the ports are alright.

---

### Post by lisati on 2014-07-30
> **noah10 said:**
> Port Forwarded yes, static no BUT should work for the time being. 
Is port forwarding set to the correct machine? It's possible that your router has assigned a new **internal** ip address to your server, which is why I suggested getting your router to reserve a local IP address.

edit: I'm wandering off to assist Mrs Lisati with some housework for a while, it could get confusing with several of us making suggestions. I'll check in again later.

---

### Post by noah10 on 2014-07-30
> **lisati said:**
> Is port forwarding set to the correct machine? It's possible that your router has assigned a new **internal** ip address to your server, which is why I suggested getting your router to reserve a local IP address.
Yes the ports are forwarded to the right machine. I only have 3 on right now and am looking at the router page as i type this.

---

### Post by CharlesA on 2014-07-30
Double check the config with something like canyouseeme. [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by lisati on 2014-07-30
> **CharlesA said:**
> Double check the config with something like canyouseeme. [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Nice. :D

---

### Post by SeijiSensei on 2014-07-31
According to the "whois" record for noahpcfreak.info, name service is provided by ns1.noahpcfreak.info and ns2.noahpcfreak.info.  Neither of those names resolves to an IP address, so no one out here can find any information about your site.  You need to add the appropriate A records that point from names like [www.noahpcfreak.info](www.noahpcfreak.info) to their corresponding IP addresses.  To do that you'll need to talk to your domain registrar.

---

### Post by Doug S on 2014-07-31
> **SeijiSensei said:**
> According to the "whois" record for noahpcfreak.info, name service is provided by ns1.noahpcfreak.info and ns2.noahpcfreak.info.  Neither of those names resolves to an IP address, so no one out here can find any information about your site.  You need to add the appropriate A records that point from names like [www.noahpcfreak.info]("http://www.noahpcfreak.info") to their corresponding IP addresses.  To do that you'll need to talk to your domain registrar.Seiji: That is different than before. [www.noahpcfreak.info]("http://www.noahpcfreak.info") did resolve to an IP address. I agree that now it does not.

---


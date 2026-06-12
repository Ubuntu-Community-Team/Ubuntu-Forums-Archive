---
title: "Server Not Routing"
date: 2009-08-01
forum: Server Platforms
---

### Post by oliv2915 on 2009-08-01
I am setting up a home server for routing. I have the DHCP setup and giving IP address but I am not getting internet on the other systems in the network. I know there needs to be a NAT installed and IP tables setup but I have no clue on where to start.

---

### Post by hictio on 2009-08-01
This [Ubuntu Server Guide + Firewall](https://help.ubuntu.com/8.10/serverguide/C/firewall.html) should be a nice place to begin your reading.
Specially the "IP Masquerading" section.

Yes, yo do need to do enable masquerading on your iptables rules, but also, you need to enable the routing function, or ability, on the Linux box that is serving as router, by default it is disabled.

---

### Post by oliv2915 on 2009-08-01
Thanks, that helped alot. I now have DHCP and routing working using UFW. My nest quetions is how do I setup squid for caching and proxy. I am willing to do reading as I am learning as the same time. I just need pointers that is all.

---

### Post by wojox on 2009-08-01
Same area :

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

There are docs for everything.

---

### Post by oliv2915 on 2009-08-01
Thanks, I will read it and see what I can do. I will be have I have any problems.

I may not have been the 1st or last person to say this but this site has a very large wealth of information for newbie linux users.

Edit: I forgot to ask if Squid does Caching by default or do I have to enable that? From what I am reading it only shows you how to setup the proxy side not caching.

---


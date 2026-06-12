---
title: "Basic firewall/content filtering set up"
date: 2015-02-11
forum: Security
---

### Post by zoomiest2 on 2015-02-11
This is a bit of a newbie question, but... I have been using Linux for a  long time, and I can't get a firewall box operational.  Here is my configuration. What am I doing wrong?

GOAL: I am trying to implement the content filtering on all traffic, so ... filter all traffic before it goes to the wifi/router.

_SET UP_: 
Cable Modem > firewall box > Linksys Wifi/Router

_ADDRESSING for above_:
192.168.**0**.x    >   **eth0**: 192.**1**68.0.x,   **eth1**: 192.168.**1**.x  > 192.168.**1**.x

_PROBLEM_:
I can't get traffic to go through the firewall box to the Linksys router.

Is the addressing okay? (do all devices need to be on the same subnet?) 

I have also consistently NOT been able to access the management console from across the network

Is there a known approach to static/dhcp settings? Perhaps DHCP for all interfaces is best?

Should I reboot all devices in series to reset them?

Thanks for your help.

---

### Post by wannabe user on 2015-02-11
At the moment they're technically on different networks, assuming you're using standard class C - 255.255.255.0 (/24). So for your current setup I think you would require a route betweem them, for example:
```

route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth1
route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1 dev eth0

```

---

### Post by zoomiest2 on 2015-02-11
Okay, so the **_typical_** way to set them up is to keep all interfaces on the same subnet? (only use 192.168.**0**.x range for all interfaces above?)

But, I would likely put the internal network (dhcp from the linksys network to users) on a another subnet? Please confirm. (e.g. 192.168.**1**.x)? (appreciate these answers!)


BTW, where would I implement your routing script above?

---

### Post by wannabe user on 2015-02-11
It's difficult to say what is typical, purely because you could argue there's not a typical deployment. It's not uncommon for a firewall to perform routing as well, it's what most of the distros do such as pfSense and Smoothwall etc. 

The route commands I posted would be issues on the firewall/Ubuntu box. Basically it's saying find this network by going to this interface, they're just static routes. You can run:
> 
route


From a terminal and you'll find your default gateway listed.

Here's a link to something to read about routes which may be worth trying if no one gives you a more specific answer:
[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by zoomiest2 on 2015-02-11
Thank you.

... as long as putting all devices (cable modem + firewall box + wifi router) on the same subnet doesn't commit some large security blunder... which is what I was worried about. Much appreciated!

Also, thanks for the reading reference.

---

### Post by Doug S on 2015-02-12
Here is what I did for my internal network: 

For what you call "firewall box", I have my main Ubuntu server. It is my router, firewall, DHCP server, internal DNS, and some other things. I use iptables to handle all traffic.

Where you have "Linksys Wifi/Router", I do also, except that I configured mine to be a switch instead of a router. So, I don't have to think about Wifi, as the Linksys takes care of it. The linksys also has a static IP address on my LAN sub-net, so that I can still access it.

---

### Post by SeijiSensei on 2015-02-12
To make all this work transparently takes a bit of work.

1) By default, Ubuntu will not forward packets across interfaces.  You need to remove the hash mark from the line "net.ipv4.ip_forward=1" in /etc/sysctl.conf, then reboot.

2)  You'll need to enable "masquerading" on the Linux box by adding the line
```
/sbin/iptables -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.0.1
```
to /etc/rc.local and rebooting. That makes all the traffic from machines behind the Linux box appear to be coming from 192.168.0.1.

2) I'm not sure what kind of "content filtering" you're talking about.  Are you using Squid?  In a "transparent" setup?  If so, then you need another iptables rule in rc.local:
```
/sbin/iptables -A PREROUTING -s 192.168.1.0/24 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128 
```
This intercepts traffic intended for remote web servers (port 80) and pushes it through the local machine's port 3128, the default port Squid listens on.

3)  A much simpler solution is just to put the Linux box on the same network as the other machines and configure the clients' browsers to use the proxy.  In Firefox, that's in Edit > Preferences > Advanced > Network > Settings (or Tools > Options > etc. on Windows).  Of course, users can disable that feature and avoid the filtering which is why transparent proxying is preferable.

---

### Post by zoomiest2 on 2015-02-12
Ah! Thank you!

---


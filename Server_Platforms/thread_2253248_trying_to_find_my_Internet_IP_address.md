---
title: "trying to find my Internet IP address"
date: 2014-11-18
forum: Server Platforms
---

### Post by grier-devon on 2014-11-18
So I just setup an Ubuntu Server 14.04.1 and I cam currently running owncloud, the issue that I am running into is that the server is in my local network so when I do an "ifconfig" I get an IP address for inside my network so anytime my laptop or phones leave the wifi I lose the connection. How do I obtain the internet IP address so my devices can connect when away from home? Thanks.

---

### Post by TheFu on 2014-11-18
You can ask google. Just query "my ip" - there's ipchicken.com or you can query the edge router too.
However, most ISPs do not provide an IP that doesn't change for free, so expect it to change.  Sometimes that is once every 5 years and other times it is 4 times a day. The frequency is up to the ISP.

You can use a "dynamic DNS service" to have a name-based way to contact your server or you may be able to pay the ISP to get a "static IP" - residential plans generally do not allow this.  If you go with dyndns - check which services your router may support. That will be the easiest way.  I've been using dnydns,org for 15+ yrs (grandfathered), but they recently made it harder.  no-ip.com is another - and there must be 50 others that you can select.

Of course, you already know about opening router ports [http://www.howtogeek.com/66214/how-to-forward-ports-on-your-router/](http://www.howtogeek.com/66214/how-to-forward-ports-on-your-router/) and that the owncloud provided in the Ubuntu repos is full of critical security issues. [http://www.webupd8.org/2014/10/owncloud-ubuntu-package-affected-by.html](http://www.webupd8.org/2014/10/owncloud-ubuntu-package-affected-by.html)  If you don't want your network to be "pwned" - use a VPN to access owncloud. Something like openvpn with ipsec.  Don't use pptp.

Some ISPs are doing double-NAT for residential IPs too - if the public IP on your router's WAN interface falls into the reserved ranges 10.x.x.x/8 or 192.168.x.x/16 or the 172.16.x.x/?? - there will not be anything that you can do to run a server from home. In some countries, this is extremely common, while it is just beginning to happen in places like the USA, in limited areas.

Hope this is all clear.

---

### Post by SeijiSensei on 2014-11-18
Click here: [http://whatismyip.com/](http://whatismyip.com/)

---

### Post by Gompa on 2014-11-19
if its a ubuntu server install its probably easier to just do:
 curl ifconfig.me
or 
curl ip.h-bomb.nl

---

### Post by xubuntu84 on 2014-11-20
Also, from the terminal:
```

wget -qO- icanhazip.com

```

---

### Post by lisati on 2014-11-20
TheFu mentioned dynamic DNS as a tool for accessing your server from outside your network. When I was running my own server the first such service I used was [no-ip.com]("http://www.noip.com/"), which served my purposes well at the time.

---

### Post by waelmagdy on 2014-11-20
use this command >>

> curl ifconfig.me


---

### Post by nerdtron on 2014-11-20
> **waelmagdy said:**
> use this command >>
> curl ifconfig.me

holy s!!!

That is even better than what I'm currently using - curl ident.me

ifconfig.me website even gives more options to choose from.

---

### Post by lisati on 2014-11-20
Unless I am mistaken, I think the OP wants to connect their devices (e.g. phone) to their home network while they're away from home.

---

### Post by TheFu on 2014-11-23
> **waelmagdy said:**
> use this command >>

This is a  really nice solution, but there are dynamic clients - ddclient and many home routers have support for the most popular dynamic DNS services.

---

### Post by sandyd on 2014-11-24
Another solution, if you have a server outside your home network with a static, public IP is simply to establish a VPN between the server outside your home network and the server inside your network hosting owncloud. You can then connect to the OwnCloud network by simply connecting to the VPN.

Side note: Running dnsmasq on the external server will allow you to resolve the owncloud address. Use something like
```

address=/hydras.secret.owncloud.instance.that.skye.cant.find/192.168.0.22
```

---

### Post by krizna on 2014-11-24
IPV4
```
curl ipv4.ipogre.com
```
IPV6
```
curl ipv6.icanhazip.com
```

---


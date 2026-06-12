---
title: "ow do you setup a dial up broadband connection on Debian?"
date: 2009-06-19
forum: Server Platforms
---

### Post by marklodge on 2009-06-19
My current setup is: 

Squid Proxy Server--------->
Client PC----------------------->   ADSL Router -------> Internet
Client PC----------------------->
Client PC----------------------->

I want the Client PC to use the Squid Proxy Server for internet.

There are 2 ways i have in mind

1st option: Set the ADSL Router into bridge mode and connect the Squid Proxy Server to the internet via a dial up broadband connection with username and password.

2nd option:Use another server as SUSE router and use that between the client and Squid Proxy Server

I want to go with the 1st option but i don't know how to do it. How do you setup a broadband connection on Debian?

Thanks
Mark

---

### Post by cariboo on 2009-06-20
If I remember correctly, Debian gives you the choice of setting up either dhcp or a static ip address during setup. You want to setup a static ip address on your server. Your /etc/network/interfaces file should look something like this:

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address		192.168.1.250
netmask		255.255.255.0
broadcast	192.168.1.154
gateway		192.168.1.1
```

You will have to setup the ip address, broadcast and gateway addresses to reflect your setup. Once the /etc/network/interfaces file is set up, all you should have to do is to restart networking:

```
sudo /etc/init.d/networking restart
```

---

### Post by marklodge on 2009-06-20
Sorry, i have not made myself clear. 

I need to have a broadband dial up connection that uses a Username and Password.

Thanks

---

### Post by kustomjs on 2009-06-20
do you mean a PPPOE connection?

PPPOE= dial over ethernet connection aka (Point-to-Point Protocol over Ethernet).

You Would Need a other computer doing the radius, authorization.

here is a how to: [http://www.freeantennas.com/PPPoE-Server-HOWTO.html](http://www.freeantennas.com/PPPoE-Server-HOWTO.html)
[http://www.netup.biz/article-pppoe-server.php](http://www.netup.biz/article-pppoe-server.php)
[http://docs.huihoo.com/darwin/opendarwin/articles/network_config/ar01s04.html](http://docs.huihoo.com/darwin/opendarwin/articles/network_config/ar01s04.html)

---

### Post by marklodge on 2009-06-20
> **kustomjs said:**
> do you mean a PPPOE connection?

Yes, a PPPOE connection.

How do you do it?

---

### Post by kustomjs on 2009-06-20
I just posted some links up:

this is how to setup pppoe connection but if you want to know how to setup pppoe server look at my links on the last post.
[http://tldp.org/HOWTO/PPP-HOWTO/](http://tldp.org/HOWTO/PPP-HOWTO/)

---


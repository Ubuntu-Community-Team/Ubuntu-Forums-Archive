---
title: "Hosting a webpage on your own server."
date: 2009-07-16
forum: Server Platforms
---

### Post by irv on 2009-07-16
I remember back when I was thinking about hosting my own website on my own server but didn't know how to go about doing this. So I did a search on the web looking for all the answers so I could get it setup right. Because of this and seeing newbies on this forum asking question about trying this same thing I thought I would put together this post to maybe answer some of the questions they might be asking. If any one wants to add to this feel free to do so. With that said here is how I got my website to be hosted on my own server.
First I got a static ip address from my service provider, then I got a domain name and had the domain name bound to that ip address. Here is the screenshot to how I bound it on the Domain Name Server (DNS).
[ATTACH]121263[/ATTACH]
Next I setup my router that allow me to host that ip address. This allow anyone who types my URL in a browser which point my URL to that ip address on the DNS and in turn finds my ip address on my router. Again here is a screenshot.
[ATTACH]121264[/ATTACH]
Next I had to give my server a static ip address on my network so I could open all the ports in the router for http, ftp, etc. Again here is a screenshot:
[ATTACH]121265[/ATTACH]
The only thing left now was to setup the server which I am not covering in this thread. But after you do this you should be able to host your own web. 
My DNS was with 1and1 and my router was a Linksys.
Hope this will help some newbie out here.

---

### Post by Thirtysixway on 2009-07-17
One thing you may want to put in your guide is howto setup a static lan IP for your server.

Right now (at least telling by your screenshots) you're forwarding your ports to 192.168.1.105.  By default this is in dhcp range of linksys routers, so I'm assuming your server is using dhcp.  While this works for a while, dhcp can change that IP, and thus breaking your port forwarding settings.

You can edit the settings for your network card by modifying /etc/network/settings file.  Here's mine:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.10
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

As you can see, I set it to stop using dhcp to obtain an IP, and gave it a static IP address 192.168.1.10.  This is outside of the linksys' default dhcp range (starts at 192.168.1.100 and goes up) so any computer on the network using dhcp won't cause any issues trying to obtain the IP.

So after you do this, set your port forwarding to 192.168.1.10 and don't worry about dhcp breaking access to your server ;)

You can use any 192.168.1.x as long as x isn't 0, 1, 255, or anything above 99 because that's when you start getting into dhcp range.

---

### Post by irv on 2009-07-18
Yes, you have a good point, I did do this but didn't cover that in my first post. You do need a static IP address on your server. Any server I have setup I always gave it a static IP address.
Thanks for the addition it is well accepted. 
Irv

---


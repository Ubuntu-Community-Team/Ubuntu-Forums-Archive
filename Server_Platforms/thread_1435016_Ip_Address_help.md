---
title: "Ip Address help"
date: 2010-03-21
forum: Server Platforms
---

### Post by Vorksholk on 2010-03-21
Hello, sorry this will be a little short, but, OK. So, I downloaded and installed Ubuntu 9.10 Karmic Koala Server Edition, installed the GUI, and then now want to host a website. Internally, my IP is 192.168.0.8/, which works just fine, but my external one is 174.28.73.81, which does not work. Why is this? What can I do to fix this? I went to [http://whatismyip.com/](http://whatismyip.com/) and got this IP, and it seems to be the IP for my network, because I get the same address no matter what computer (on my network) I try it on. Any help is greatly appreciated.

---

### Post by Lucky. on 2010-03-21
Most Internet connections are single IP address only.  As you probably already know, your 174.28.73.81 address is your "real" IP address.  The 192.168.0.8 address is a private internal address.

Your router uses NAT/PAT to share your single external IP address between all of the computers on your internal network.  This is why when you use any computer and visit [http://whatismyip.com/](http://whatismyip.com/), you get the same address.  No computer on your private home network is actually at 174.28.73.81.  Your router's external/WAN port is at 174.28.73.81, and it's just sharing it all on the inside.

It is "impossible" for someone to go directly to your 192.168.0.8 server, because the range of 192.168.0.0 to 192.168.255.255 is [classified as private](http://en.wikipedia.org/wiki/Private_network).  I have a server at 192.168.1.10 myself.  Lots of us have 192.168.0.0 networks.  Thousands of us have the same private IP address, but that's ok because they're *private*.  However nobody else in the world should have your 174.28.73.81 address.

In order to get your web server accessible from the Internet, you'll have to configure your router to do some sort of port forwarding / DMZ type of game to translate 174.28.73.81 to 192.168.0.8.  I wish I could tell you how, but every router is different.  It's not terribly too hard to dink around and find the setting if your router supports it (and lots do!).

The only extra catch is that your external IP address (174.28.73.81) will probably change over time because of DHCP.  Turning your router off/on, unplugging cables, server hiccups on the ISP side, etc...that IP address will change.  One day you may find yourself going to 174.28.73.81, and it just won't work anymore.  In order to accommodate for this, try using an dynamic DNS service.  DDNS assigns you a domain name that maps to your IP address and changes when your IP address changes.  If your router supports dynamic DNS, it will phone home to a dynamic dns server (after you set up an account) and keep it informed when your IP address changes.

Good Luck!

---

### Post by Vorksholk on 2010-03-21
OK, so I have an AirPort Base Station a/b/g/n^draft which gets internet from a Qwest modem, which should I do the port forwarding on? :) Thanks!

---

### Post by Iowan on 2010-03-21
If your Qwest modem also acts as a router/firewall, that would be where to port-forward.

---

### Post by Vorksholk on 2010-03-21
Thanks! And how do I port-forward? :)

---

### Post by lisati on 2010-03-21
> **Vorksholk said:**
> Thanks! And how do I port-forward? :)

The exact details vary from router to router. Most have a browser-based configuration page which can be used to change your settings. What model router are you using? Someone with a similar one might be able to point you in the right direction.

---

### Post by Vorksholk on 2010-03-21
I have a Qwest Actiontec M1000.  I don't know what to enter for port IP range.... :( :

---

### Post by koenn on 2010-03-21
you want to forward /, which works just fine, but my external one is IP (174.28.73.81 : port 80 ) to 192.168.0.8 : port 80


[http://www.qwest.com/internethelp/modems/m1000/modemDetail_M1000_advanced.html](http://www.qwest.com/internethelp/modems/m1000/modemDetail_M1000_advanced.html)

instructions under  "# Port Forwarding 80 (Web Server)* " a.o.

---

### Post by Vorksholk on 2010-03-22
Thanks for all of your help!

---

### Post by Iowan on 2010-03-23
> **Vorksholk said:**
> I have a Qwest Actiontec M1000.  I don't know what to enter for port IP range.... :( :Hey! I have one of those, too...
Haven't done port forwarding yet, though.

---


---
title: "Port forwarding from one machine to another."
date: 2008-09-02
forum: Server Platforms
---

### Post by KingJohn on 2008-09-02
Hi,

I have a router which is very stupid, and can't use PAT.  Meaning, it can only forward port 443 to one single device on the internal network, and it cannot forward other external ports to 443 internally.  It is 192.168.1.1.

I have a device that is very stupid, and can only listen on port 443.  It is 192.168.1.251.

I have an HTTPS server on the LAN, and I don't *want* to make it listen on a different port just to accomodate the very stupid device.  It is a Ubuntu 8.04.1 LTS Server machine, and can do anything I want it to.  It is 192.168.1.4.

My plan is this:
1) have the router forward port 999 to the server.
2) have the server listen on port 999 and seamlessly redirect the 999 traffic to 443 on the device
3) have the device listen on 443, handle everything happily, and respond either to the server (which then responds to the original client) or directly to the client.

Thing is, I can't actually make this work.

I've tried netcat - > nc -l -p 999 | nc 192.168.1.251 443 | nc -b -l -p 999fails because the third NC, to bind the returning traffic, can't grab port 999.  And I'm not sure how to fix it.

I've tried iptables - 
> iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -d 192.168.1.251 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -m tcp -d 192.168.1.4 --dport 999 -j DNAT --to-destination 192.168.1.251:443

Again, no luck.

I even got desperate, and tried SSH port forwarding:> ssh -L 999:192.168.1.251:443 root@localhostand man-in-the-middling my own HTTPS device by adding a > proxypass /device/ [https://192.168.1.251/](https://192.168.1.251/)
ProxyPassReverse /device/ [https://192.168.1.251/](https://192.168.1.251/)to the site file on the existing HTTPS server.

So:  What I want to do is REALLY EASY if you just have a router that's smart enough to take an external *AND* an internal port.
It's REALLY EASY if you have a router that's smart enough to have two external IPs.
It looks REALLY EASY on paper with iptables or ProxyPass - and yet, I'm stuck.  I've got nothing working, and I'm having trouble even finding out why my failures are, well, failing.

---

### Post by cdenley on 2008-09-02
So you want the router to port forward 999 to which server?
```

iptables -t nat -A PREROUTING -p tcp -m tcp -d 192.168.1.4 --dport 999 -j DNAT --to-destination 192.168.1.251:443

```
Why would you forward it to 192.168.1.4, then DNAT it to 192.168.1.251?

Try this
```

sudo iptables -t nat -A OUTPUT -p tcp -m tcp --dport 999 -j DNAT --to-destination :443

```
The traffic for port 999 should be forwarded to the server you run this command on.

---

### Post by KingJohn on 2008-09-02
Both my server and my new device listen on HTTPS.
The device cannot listen on a different port.
I do not want to move my server to a different port.

Right now, the firewall takes
EXTERNALIP:443 and forwards it to SERVER:443

What I *really* want is for the firewall to take
EXTERNALIP:999 and forward that to DEVICE:443

However, the router is stupid.  The router can't do port translation.

So what I'm trying to do is make the router take
EXTERNAL:999 and forward that to SERVER:999, which will forward in turn to DEVICE:443

The net result I want is that a user will type
[https://EXTERNALIP:999/](https://EXTERNALIP:999/) into their browser, and they will seamlessly see
[https://DEVICE:443/](https://DEVICE:443/)
With all traffic back and forth appropriately routed so that it works just like as if I'd forwarded 443 from the router to the device.

> Why would you forward it to 192.168.1.4, then DNAT it to 192.168.1.251?
Because I really don't know what I'm doing when it comes to iptables.  I am trying to run this from 192.168.1.4

> Try this

[QUOTE]sudo iptables -t nat -A OUTPUT -p tcp -m tcp --dport 999 -j DNAT --to-destination :443

The traffic for port 999 should be forwarded to the server you run this command on.[/QUOTE]

Don't I have to specify an IP with --to-destination?  Otherwise, how it know to take incoming port 999 traffic and sent it to *the right server* on 443?

Still.  running "iptables -t nat -A OUTPUT -p tcp -m tcp --dport 999 -j DNAT --to-destination 192.168.1.251:443" as root doesn't solve my problem, nor does doing it without the destination IP.  In both cases, traffic still isn't getting forwarded from server:999 to device:443 and back.

---

### Post by cdenley on 2008-09-02
> **KingJohn said:**
> Both my server and my new device listen on HTTPS.
The device cannot listen on a different port.
I do not want to move my server to a different port.

Right now, the firewall takes
EXTERNALIP:443 and forwards it to SERVER:443

What I *really* want is for the firewall to take
EXTERNALIP:999 and forward that to DEVICE:443

However, the router is stupid.  The router can't do port translation.

So what I'm trying to do is make the router take
EXTERNAL:999 and forward that to SERVER:999, which will forward in turn to DEVICE:443

The net result I want is that a user will type
[https://EXTERNALIP:999/](https://EXTERNALIP:999/) into their browser, and they will seamlessly see
[https://DEVICE:443/](https://DEVICE:443/)
With all traffic back and forth appropriately routed so that it works just like as if I'd forwarded 443 from the router to the device.


Because I really don't know what I'm doing when it comes to iptables.  I am trying to run this from 192.168.1.4



Don't I have to specify an IP with --to-destination?  Otherwise, how it know to take incoming port 999 traffic and sent it to *the right server* on 443?

Still.  running "iptables -t nat -A OUTPUT -p tcp -m tcp --dport 999 -j DNAT --to-destination 192.168.1.251:443" as root doesn't solve my problem, nor does doing it without the destination IP.  In both cases, traffic still isn't getting forwarded from server:999 to device:443 and back.

I incorrectly assumed both servers were linux servers with iptables. Maybe the reason you are still having problems is because of the source address of the forwarded packets.
```

sudo iptables -t nat -A PREROUTING -p tcp -m tcp --dport 999 -j DNAT --to-destination 192.168.1.251:443
sudo iptables -t nat -A POSTROUTING -p tcp -m tcp -d 192.168.1.251 --dport 443 -j SNAT --to-source 192.168.1.4:999

```
Also, you might have to enable IP forwarding
```

sudo -s
echo 0 > /proc/sys/net/ipv4/ip_forward
exit

```

---

### Post by lazyart on 2008-09-02
No chance of just getting another router?  That's a lot to do when $40 or so can make it all go away...

---

### Post by Vivaldi Gloria on 2008-09-03
I came across something about netcat that might interest you. Search "mknod backpipe p" in the following pages:

[http://www.stuvel.eu/archive/25/two-way-tunnelling-with-netcat](http://www.stuvel.eu/archive/25/two-way-tunnelling-with-netcat)
[http://mail.python.org/pipermail/python-list/2006-August/397392.html](http://mail.python.org/pipermail/python-list/2006-August/397392.html)
[http://www.ethicalhacker.net/component/option,com_smf/Itemid,54/topic,2075.msg8407/#msg8407](http://www.ethicalhacker.net/component/option,com_smf/Itemid,54/topic,2075.msg8407/#msg8407)
[http://clug.net.nz/index.php/netcat](http://clug.net.nz/index.php/netcat)
[http://forums.remote-exploit.org/showthread.php?t=14042](http://forums.remote-exploit.org/showthread.php?t=14042)
[http://www.softpanorama.org/Net/Netutils/netcat.shtml](http://www.softpanorama.org/Net/Netutils/netcat.shtml)

I haven't tried this myself so I cannot comment on it.

---

### Post by KingJohn on 2008-09-05
Solved the problem, actually.

The magic fix is rinetd

Step 1:
install rinetd
> apt-get install rinetd

Step 2: 
edit /etc/rinetd.conf to include the line
> 192.168.1.4 999 192.168.1.251 443at the appropriate place - the default empty config file will show you.

Step 3:
restart rinetd to notice the new config file.
> /etc/init.d/rinetd restart

Problem solved!  Port forwarded!  Everything works perfectly!

---

### Post by Vivaldi Gloria on 2008-09-05
Thanks. I didn't know about rinetd. Here are some links for future reference:

[[COLOR="Sienna"]howtoforge[/COLOR]]("http://www.howtoforge.com/port-forwarding-with-rinetd-on-debian-etch")

[[COLOR="DarkOrange"]ubuntugeek.com[/COLOR]]("http://www.ubuntugeek.com/rinetd-redirects-tcp-connections-from-one-ip-address-and-port-to-another.html")

[[COLOR="Olive"]debian-admin[/COLOR]]("http://www.debian-administration.org/articles/601")

---

### Post by rybing on 2012-12-26
This post helped me a lot.  My situation:

I needed to forward rdp (port 3389) traffic from an ubuntu 12.04 LTS server connected to a remote Cisco SSL vpn using openconnect.  Ultimate goal: I wanted to connect from a chromebook (which doesn't support ssl vpn) to a windows terminal server at work.

I tried all the iptables combinations I could find on google and nothing worked.  Installed rinetd per the instructions in this thread, modified the conf file, restarted the service, started up the VPN and voila!  It works!!  Now I can just use chrome rdp to connect to my linux box and it passes right through the vpn connection to the windows terminal server.

Thanks so much to the original posters!

---


---
title: "[SOLVED] APACHE is giving me Hell"
date: 2008-04-08
forum: Server Platforms
---

### Post by AlexandroM on 2008-04-08
I have just installed a fresh Ubuntu 7.10 server om my machine.
I didn't have the installer perform the LAMP istall, only OpenSSH. So it is completely clean.

It is placed behind a firewall running pfSense and ports 80 and 443 are forwarded to my Ubuntu machine.

83.80.68.138 is my outside address
192.168.24.222 is my Ubuntu address

The NAT on my router works fine when I forward to other computers on my network and on a previous install of ubuntu on the same machine I could reach Webmin, Tomcat, CUPS etc...
So all is well but Apache is unreachable form outside the network. It is reachable form inside offcourse.

The problem also isn't that the router won't let me see internal servers via an external request on my browser. I checked form other locations and I get the same browser-error saying that the site is unreachable.

I've looked on all the forums and I knwo what to configure in all the *.conf files but can someone please walk me through it to be sure I'm doingit the right way.

So I've got a clean install with the ports forwarded. I guess I'll go ahead and install apache2 again and then someone need to help me because apparantly something goes terribly wrong after that.

Thanx is advance for anyone with the time to help.
:confused::confused::confused:

---

### Post by hyper_ch on 2008-04-08
apache listens to port 80.... so when when it's not working from outside then the router does not forward the according port to your apache machine.

---

### Post by Mithrilhall on 2008-04-08
Can you get to your apache website from inside your network? If so then I would think the problem is with your router.

---

### Post by AlexandroM on 2008-04-08
Well that's what I tried to say in my first post. It does.
When I change the forwarding to port 631 for example, I get the CUPS admin page just fine. Likewise with the Tomcat admn page on 8080 adn webmin on 10000.

I don't have those installed now in fear of them being an interferance (higly unlikely but hust to be sure).

Any other suggestion:(

---

### Post by AlexandroM on 2008-04-08
Again all my other NAT's work just fine and I tried having Apache listen on another port and forwarding that but no game.

---

### Post by Mithrilhall on 2008-04-08
Change Apache to run on 8000 or some other port and see if that works.

Could your ISP be blocking port 80 so you can't run your own webserver?

---

### Post by AlexandroM on 2008-04-08
I changed ports.conf form Listen 80 to Listen 8000.
I forward ext. port 80 to int. port 8000.
Restart server, check on internal network on port 8000, OK.
Check external access
No game.

Could you check [http://83.80.68.138/](http://83.80.68.138/) just to be sure.

---

### Post by AlexandroM on 2008-04-08
To reply to you later question. No, my ISP is not blocking anything.
I wish it were so then changing ports was all I needed to do.
I'm on a 155Mb fibre optic ring with all ports open and have a pfSense (FreeBSD) firewall between the outisde world and my Ubuntu machine.

---

### Post by AlexandroM on 2008-04-08
Firthermore if I run IIS on a windows machinet and forward to that machine on the network then everything works fine so no problems with my firewall/router

---

### Post by cdenley on 2008-04-08
Did you configure iptables to filter incoming requests?
```

sudo iptables -L -n

```

Does your server receive the web requests?
```

sudo apt-get install tcpdump
sudo tcpdump -i eth0 tcp port 80

```

Do you have multiple network connections? Maybe it is listening on the wrong one.
```

netstat -lt

```

---

### Post by AlexandroM on 2008-04-08
First:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Second:

Nothing, only via internal IP i get a shitloed of data.

Third:

tcp        0      0 192.168.24.222:www      *:*                     LISTEN
tcp6      0      0 *:ssh                                *:*                     LISTEN

What do you make of it?

Thanx for the great tips.

---

### Post by cdenley on 2008-04-08
If tcpdump doesn't show any external web requests, then that means it isn't receiving any on that network interface.

Do you have mutliple network interfaces?
```

ifconfig

```

---

### Post by AlexandroM on 2008-04-08
eth0      Link encap:Ethernet  HWaddr 00:19:DB:5E:73:93
          inet addr:192.168.24.222  Bcast:192.168.24.255  Mask:   255.255.255.0
          inet6 addr: fe80::219:dbff:fe5e:7393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:218753 (213.6 KB)  TX bytes:393928 (384.6 KB)
          Interrupt:18 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by cdenley on 2008-04-08
Your server is working correctly. Your router is not. The external web requests are never received by your server (shown by the tcpdump command), so your router must not be forwarding them to it. If you can get the router to forward incoming traffic on port 80 to 192.168.24.222:80, then it should work.

---

### Post by AlexandroM on 2008-04-08
This seems logical. This is also what I have been working on for the last two days. I will try some more settings.

---

### Post by AlexandroM on 2008-04-08
can you try [http://83.80.68.138/](http://83.80.68.138/)
I think it works

---

### Post by AlexandroM on 2008-04-08
Everything is working now. Your tips on the TCPdump solved it.
You were right and I was right. I'll explain.

No requests were coming in at the ubuntu machine but when i direct port 80 at another machine everything was fine. Strange right?

Well the firewall is use (pfSense on FreeBSD) is based on iptables I think. Anyway I had old NAT rules pointing to my old server. When I changed my NAT tables it didn't delete my old rules for some reason.

So thye stayed higer up in rank so my firewall kept trying to connect to my old machien which I switched off. I deleted all my tables and rules and added only the one i need active now and pfSense did a great job and generated the rules too.

Everything is fine now.

Thanx.

---

### Post by cdenley on 2008-04-08
> Well the firewall is use (pfSense on FreeBSD) is based on iptables I think
It actually uses OpenBSD's packet filter. Glad to help.

---


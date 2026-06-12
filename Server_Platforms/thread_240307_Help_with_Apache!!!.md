---
title: "Help with Apache!!!"
date: 2006-08-20
forum: Server Platforms
---

### Post by baylorbear on 2006-08-20
Guys I'm stuck...

I've got apache running and an account with dyndns.com.  Apache is running because I can go to [http://localhost/](http://localhost/) ... and the dyndns.com website has the appropriate IP address for my server.

I've phoned my ISP and they've assured me that they don't block port 80 -- but just to be sure I went ahead and tested with port 8888 also -- and still nothing.

I still cannot access my server from the internet -- even when I try to use the direct IP address.

BTW -- port forwarding IS enabled on my router... (ports 80 and 8888 from where I tested it).

PLEASE HELP!

---

### Post by Glut on 2006-08-21
Check what apache is listening on (as root):
[COLOR="SeaGreen"]sudo lsof -i|grep apache[/COLOR]
It should end in something like: TCP *:www (LISTEN)
[COLOR="DarkRed"]If this fails, the problem is with your apache setup[/COLOR]
Check your firewall:
[COLOR="SeaGreen"]sudo iptables -L[/COLOR]
Unless you've installed a firewall, it should have 3 accept entries.
[COLOR="DarkRed"]If this fails, the problem is with your firewall setup[/COLOR]
Check that the dynamic DNS address resolves correctly:
[COLOR="SeaGreen"]dig @dns-server [www.example.com](www.example.com)[/COLOR]
Should come up with your ip address
[COLOR="DarkRed"]If this fails, the problem is with your dyndns setup[/COLOR]
Try telnetting to the ip address:
[COLOR="SeaGreen"]telnet [www.example.com](www.example.com) 80[/COLOR]
You should see: 
[color="orange"]Connected to [www.example.com](www.example.com)
Escape Character is '^]'[/color]
[COLOR="DarkRed"]If this fails, the problem is with your router setup[/COLOR]

---

### Post by baylorbear on 2006-08-21
Ok, I tried everything you listed and it all checks out OK up to the very last line -- router setup is a problem.

But port forwarding works because I can use ssh with port forwarding... and I've tried forwarding port 80 and then as a last resort tried opening up all ports to my box by setting myself up as DMZ server...  still nothing. :(

---

### Post by Ahriman on 2006-08-21
There is a site [http://www.portforward.com/routers.htm]("http://www.portforward.com/routers.htm") that shows you how to properly set up port forwarding on whichever router you have. They have a big list there, so chances are high that you will find your own router. It may have a step or two that you may have overlooked; I know when I tried the first time, I missed the obvious step of assigning my server a static IP, so when it renewed it's DHCP lease, no-one could connect :)

---

### Post by baylorbear on 2006-08-21
Tried using that website and followed their directions to a T... still doesn't work.

---

### Post by Useless on 2006-08-22
Is Apache listening on port 80?  It usually is by default.  You have tested it from another local machine on your network?

---

### Post by baylorbear on 2006-08-22
Yes, I can access it internally via my internal IP address.

When I disconnect from the router and plug directly into the Cable Modem, I can successfully access my server via my public IP address.

---

### Post by Ahriman on 2006-08-28
Does your Cable Modem or Router have a web-based setup? I don't have a cable modem, but my router has web-based setup, and whenever I try and access my public IP address from home, all I get is my router's web setup page, but when I try and access it from, say, work, I get my web site.

---


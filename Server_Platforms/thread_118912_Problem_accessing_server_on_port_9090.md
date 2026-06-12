---
title: "Problem accessing server on port 9090"
date: 2006-01-18
forum: Server Platforms
---

### Post by Saarg on 2006-01-18
I have tried for a time now to get access to a newsclient(actually server. Connects as a client through a browser.) on port 9090. It works localy, but from the outside world it does not connect. I can access my apache2 server from the outside.
All forwarding through router and firewall is set up correct.
Uses dyndns.org and no-ip.org.
Do I have to open the port 9090 for external access? And how do I do this?
I appriciate all the help I can get. Kind of stuck on this one :( 
My ISP might be blocking 9090? Or the router?

I have tried to change the news program to use port 80, but that didn't work. Shut down Apache while testing on port 80.

---

### Post by Glut on 2006-01-18
Ubuntu does not have any firewalls turned on by default. Unless you have turned one on, it is most likely an ISP/router issue.

Other less likely possibilities include: entries in hosts.deny, apache configuration. Given Apache can be accessed from the outside I suspect the later is not true. Check /etc/hosts.deny for yourself.

---

### Post by Saarg on 2006-01-21
Thanks for answering :)
I got it to work, but I'm not sure what made it work ;) 
I tried to access the server through my dyndns.org address, but that just resulted in a cannot access page error. I then asked a friend who was at work to try to access the server and he got the same error.
I added port 9090 in /etc/services, but it was the same problem.
When I got to work the day after, I tried to access my server and then it worked! :???: 
So either I had to put in the port in /etc/services or my friend typed the wrong address. 
Anyway I can not access the server localy when using the dyndns address, but with IP it's working. But it's no point in going through the internet when the server is on the same network as the computer I try to access it from :)

---


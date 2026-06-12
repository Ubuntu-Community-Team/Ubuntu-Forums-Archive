---
title: "Having a problem connecting externally to my server"
date: 2006-08-10
forum: Server Platforms
---

### Post by Frappe051 on 2006-08-10
Hey guys, wondering what I could do to fix this.

I try to either access my local server through my WAN IP or through a DynDNS.com account (flstudios.ath.cx) but neither let me view the server.  This is both from other computers in my network, and outside.

Local networked computers can reach it by it's local ip, but nothing else can.  

Wondering if this is a problem with my Router, or something I can fix through apache settings.

I installed Ubuntu Server using the LAMP option.  Mabye when editing something I screwed it up?

It would be really nice if someone could help me with this problem.  I've port-forwarded & DMZ'd the server, but still can't reach it.

Thanks in advance to whoever can figure this out. :)

-Frappe051

---

### Post by JonM1827 on 2006-08-10
I have the same exact problem... I have posted wondering how to fix it, but all I have gotten so far is that I need to forward port 80... which I think I have done correctly...

Well I hope we can get this figured out sometime soon, because it's kinda starting to bug me :p

Thanks in advance for any input,
-Jon

---

### Post by Frappe051 on 2006-08-10
Well, by adding "ServerName my-IP:80" to apache2.conf, I was able to get rid of the "Setting ServerName to 127.0.0.1" error I used to get.

Still not able to connect, though.  I know for a fact that my ISP is not blocking port 80 because I just installed apache to test it and without changing ports it worked.

Would really like some help here :D

---

### Post by dxt on 2006-09-06
i have just recently installed ubuntu 6.06.1 LAMP server on a PC and plugged in a public IP from our ISP to eth0.

the linux box does not respond to PING.
sometimes it does. strange. no port forwarding from our gateway, no firewall of any sort.

has anyone solved this problem?

---

### Post by MattMckenzy on 2006-09-06
I'm having the same problem as Frappe...

I've installed the LAMP server configuration multiple times... I've also tried to install LAMP manually. I've used several guides too but nothing has worked so far...

I'm thinking it's an obvious setting in apache or something like that, because it's certainly not my router or ISP; I've hosted successfully on windows XP before.

I've been trying to figure this out for over a week, so if anybody has any help for me I would greatly appreciate it.

Thanks.
MattMckenzy

---

### Post by chrisfay on 2006-09-07
First try telneting to your web server on port 80 to make sure you have the ports open and not blocked:

```
telnet 'WAN IP' 80 
```  (replace 'WAN IP' with your own IP)

If you get a response, than you're ports are open and something else is configured incorrectly. If not, than you need to look at the routing; 

- Make sure you assigned your server box a static ip
- Check your port forwarding on your router/gateway
- Make sure Apache is listening on the port you have forwarded to
- If you have a firewall enabled on you linux box make sure you have opened the ports in that as well. 
- Possibly disable firewalls temporarily for testing

If you can't telnet using port 80, try changing Apache to listen on some random high port like 4000 or something. Don't forget to forward that port in your router/gateway, and to add it to your ip in your browser when trying to access it. If that works but 80 didn't, than your ISP blocks port 80. 

9 times out of 10 if you can't access your server from outside your LAN its due to either ISP firewalled ports or misconfigured routing; especially if you can access it from within your local network. 

If you have chosen an alternitive port to run apache make sure you add that to your IP when trying to access it externally from a browser:
xx.xx.xx.xx:8080/

---

### Post by MattMckenzy on 2006-09-07
Wow, and I was so sure that wasn't the case... >_<
Turns out my ISP does block port 80.
It works now. =1
Funny because just a month ago it wasn't blocked. >_<
Oh well, thanks a lot for the help. ^_^

MattMckenzy

---


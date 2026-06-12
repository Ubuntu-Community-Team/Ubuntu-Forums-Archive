---
title: "noob Question"
date: 2012-06-04
forum: Server Platforms
---

### Post by Watchlord on 2012-06-04
I'm sorry for asking this here, but over the years, I've gotten the most educated help here.

I have an Ubuntu server connected to a router. I use a DDNS and port forwarding setup on my router to make my website, Glype proxy, Minecraft server, and Ventrilo server available on the internet.

I am moving to a dorm next semester and, unfortunately, all I have is an Ethernet jack in the wall. I don't know how many routers/servers I will be behind in my dorm. Lets say the college doesn't specifically block the ports I need. If I keep my DDNS updated on my router and the ports forwarded from that router, can I still host my stuff on the web? or am I just screwed? If I can't, is there some workaround?

btw: No, I will not ask the college. I doubt I can talk to the right person, and I'm sure they'd just think I was crazy or call me hacker because I'm suing Linux (this happens).

---

### Post by rubylaser on 2012-06-04
It is highly unlikely that you'll be hosting a webserver on your college LAN or that non-standard ports will be open.  If you want to continue with these services, I'd suggest you find an inexpensive VPS and set the services up on that.

---

### Post by Watchlord on 2012-06-04
-I will host it if I am able.
-This is a 'what if' scenario when it comes to ports being open.
-I don't want a VPS. I have a giant rackmount server already in use. A VPS is sort of a "why bother" for me. I could just host from home and manage it remotely. The point is, I want it in my dorm.

---

### Post by CharlesA on 2012-06-04
> **Watchlord said:**
> -I will host it if I am able.
-This is a 'what if' scenario when it comes to ports being open.
-I don't want a VPS. I have a giant rackmount server already in use. A VPS is sort of a "why bother" for me. I could just host from home and manage it remotely. The point is, I want it in my dorm.

You can either ask IT what the policy is on running services or just leave the box at home and manage it remotely via SSH.

You might also ask if they can open ports up for you, but I doubt the answer will be "yes."

I would really not want the noise of a "giant rackmount server" in a dorm tbh.

---

### Post by Watchlord on 2012-06-05
I've already adressed dealing with the staff in my original post, they could barelly tell me the type of connection in the dorm. I want the server in my dorm if at all possible, noise is not a problem in my dorm. No one has tried to answer my questions yet.

---

### Post by CharlesA on 2012-06-05
> **Watchlord said:**
> I've already adressed dealing with the staff in my original post, they could barelly tell me the type of connection in the dorm. I want the server in my dorm if at all possible, noise is not a problem in my dorm. No one has tried to answer my questions yet.
The answer is no it was more than likely not work.

---

### Post by Watchlord on 2012-06-05
What would prevent it? Is there a workaround that keeps the physical equipment in the dorm?

---

### Post by CharlesA on 2012-06-05
> **Watchlord said:**
> What would prevent it? Is there a workaround that keeps the physical equipment in the dorm?
Not having access to their network to open ports would prevent it.

No workaround that I know of.

---

### Post by rubylaser on 2012-06-05
> **CharlesA said:**
> Not having access to their network to open ports would prevent it.

No workaround that I know of.

As I thought I explained in my first post, this is not going to work unless the IT staff at your college are completely incompetent or have a very open user policy (which I've never seen in any University's network that I've ever seen).  They don't want users hogging up bandwidth by running their own servers in the dorms.  Just leave the box at home as CharlesA suggested, and SSH into it.

---

### Post by HugoSerrano on 2012-06-05
> **rubylaser said:**
> As I thought I explained in my first post, this is not going to work unless the IT staff at your college are completely incompetent or have a very open user policy (which I've never seen in any University's network that I've ever seen).  They don't want users hogging up bandwidth by running their own servers in the dorms.  Just leave the box at home as CharlesA suggested, and SSH into it.

Even with very incompetent staff, it wont work...
Best option it's to try to get a connection from any operator in your dorm... if possible...

---

### Post by LHammonds on 2012-06-05
It is rather pointless to theorize about 'what if' scenarios if you have no idea what is allowed.

My suggestion would be to setup a similar environment on a laptop or at least of some way of remotely seeing if the same ports are active on your laptop and just take it with you on day #1.  Jack it into the LAN and then see what you can make work...such as using a smart phone to try and access it from the outside.  If your initial tests work (which I also seriously doubt it would), then bring in the server rack and have fun.

The reason why I say it probably will not work is that in a shared access invironment like a dorm / university, the outside world will probably only see activity from you through a single IP address on the university's firewall.  People on the outside will hit the firewall and the firewall will not know "how" to route traffic to your server (IP) without any rules defined.

Outbound traffic works because of an established session from your LAN IP to the firewall but there is no such session when requests originate from the outside.

So basically, you will need to find out who handles the university's firewall and buddy-up with them if you want to stand any kind of chance getting this to work.

LHammonds

---


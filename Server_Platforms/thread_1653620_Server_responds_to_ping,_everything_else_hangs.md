---
title: "Server responds to ping, everything else hangs?"
date: 2010-12-27
forum: Server Platforms
---

### Post by never gonna give you up on 2010-12-27
Hello Ubuntu Community,

Throughly stumped here. I'm a college student home for winter break and I've got a server sitting on my desk at school that I thought was working when I left. However, upon arriving home, I checked the server to find that it doesn't work -- not even a 404 page or a time out error, the browser just hangs. To use anything other than HTTP on port 80, I need to be on a VPN.

I log into the VPN and start with the basics. The machine (which is not behind a router) responds to ping, however ssh shows the same symptoms as apache. I don't even get a connection refused or path not found or timeout error, the login literally just hangs (have had it hanging for like 30 min now).

After being thoroughly baffled by this, I ran NMAP from another machine on the same network:

```

[luke@xxxxxxx ~]$ nmap -A -T4 xxxxxx

Starting Nmap 4.11 ( http://www.insecure.org/nmap/ ) at 2010-12-27 03:39 EST
Interesting ports on xxxxx.stu.rpi.edu (128.113.xx.xx):
Not shown: 1676 closed ports
PORT    STATE SERVICE  VERSION
21/tcp  open  ftp?
22/tcp  open  ssh?
80/tcp  open  http?
111/tcp open  rpcbind?

```

I have VPN access and control over other computers on the same network, but no physical access to the machine. Any ideas what is going on or how I can get at this thing? Was really hoping to have my website up so I can show off my work when applying for jobs over the break ;)

Thanks for your help!

ninja edit: omitted my IP addresses and whatnot

---

### Post by EmanresuusernamE on 2010-12-27
I had a problem like this once.  Check your firewall and make sure you're allowing all of the traffic that you want through to your server.  I blocked myself using Shorewall on accident and couldn't get in unless the server was restarted, I didn't have Shorewall run at startup which would allow me to have someone restart the machine and then I could remote in.

Your firewall shouldn't block anything "local" such as the VPN by default for the most part. Your VPN traffic seems to be bypassing the firewall and your remote traffic seems to be hitting it.

---

### Post by EmanresuusernamE on 2010-12-27
And personally, when I'm on my server, I have nmap look at "localhost" instead of the IP address to ensure it's looking at itself, make output copy and pastable and to avoid typing out the full IP address. :)

---

### Post by Justin_Ferrell on 2010-12-29
Your server could be behind a IDS (Example Snort) that blocks suspcious traffic from coming in. Also, I dont see the common VPN port on your nmap report. (TCP 1723) . Are you VPN into your schools network then trying to connect to your server? Or are you trying to connect directly to your server? Try also doing a tracert with hostname resolution to see if there is any other device that could block connections

---


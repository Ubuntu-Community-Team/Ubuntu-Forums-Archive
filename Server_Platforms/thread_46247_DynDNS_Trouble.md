---
title: "DynDNS Trouble"
date: 2005-07-03
forum: Server Platforms
---

### Post by _cashel on 2005-07-03
I'm running my linux server as a TeamSpeak server. I setup an account @ DynDNS and am using their Dynamic IP service. This was working fine untill  last night when I had to switch routers. The server is able to access the internet, and I'm able to access it through PuTTy locally, but I cannot access it through it's DynDNS address. I never had to enable or add anything to my last router, so I've done nothing to this one. When I run the dig -i command, I don't pull up an external IP, but instead, I pull up 192.168.0.1: the address of the router. The previous router was a D-Link DI-704UP and the current one is a DI-624. Any thoughts on what's going wrong here?


edit: I forgot to add: on my account page, it says that the IP hasn't been updated since switching out routers. This isn't true though because I have run it several times since then.

---

### Post by dickohead on 2005-07-03
[QUOTE=_cashel]I'm running my linux server as a TeamSpeak server. I setup an account @ DynDNS and am using their Dynamic IP service. This was working fine untill  last night when I had to switch routers. The server is able to access the internet, and I'm able to access it through PuTTy locally, but I cannot access it through it's DynDNS address. I never had to enable or add anything to my last router, so I've done nothing to this one. When I run the dig -i command, I don't pull up an external IP, but instead, I pull up 192.168.0.1: the address of the router. The previous router was a D-Link DI-704UP and the current one is a DI-624. Any thoughts on what's going wrong here?


edit: I forgot to add: on my account page, it says that the IP hasn't been updated since switching out routers. This isn't true though because I have run it several times since then.[/QUOTE]
 perhaps on the other router you had port-forwarding or similar setup? You would have to re-enable this. Routers connect two networks together, as you know, so if you are running services on a local server that are to be served out across the internet when someone requests your internet IP (234.217.237.212 - just an example) from a web browser, DynDNS will translate the name: yourserver.com to the address, but if the router doesn't know what to do with request on say: port 80 - being the port HTTP uses, then it will do nothing. So on your router you need to forward port 80 to the IP address of your server. ie:

234.217.237.212:80 - 192.168.1.X

I'm not entirely clear on exactly how DynDNS works, since I'm lucky enough to have a static IP, but if you had it working once, I assume you can get it going again...?

---

### Post by _cashel on 2005-07-03
Enabling port forwarding for port 80 doesn't seem to have any effect on the DynDNS issue :(

---

### Post by deuce868 on 2005-07-03
[QUOTE=_cashel]Enabling port forwarding for port 80 doesn't seem to have any effect on the DynDNS issue :([/QUOTE]

I'm giong to be that teamspeak doesn't run on port 80.

---

### Post by _cashel on 2005-07-03
[QUOTE=deuce868]I'm giong to be that teamspeak doesn't run on port 80.[/QUOTE]


No, it doesn't. I was just enabling that for DynDNS as that's what was suggested on both the site and in this thread. I should have forwarded the TS ports earlier as well. However, forwarding all of these ports hasn't fixed anything.

---

### Post by dickohead on 2005-07-04
[QUOTE=_cashel]No, it doesn't. I was just enabling that for DynDNS as that's what was suggested on both the site and in this thread. I should have forwarded the TS ports earlier as well. However, forwarding all of these ports hasn't fixed anything.[/QUOTE]
 Can you access your server by typing in your remote IP Address? IE - you can access it through your local network, what about with your Internet IP? If not - then it's your router, if you get access to it - it's DynDNS, DynDNS requires that you somehow notify them (automatically) when your IP address changes, chances are pretty good this needs to be done on the router - some routers can be configured to do it automatically, some need it done manually.

I was using port 80 as an example, you would have needed to find the ports for whatever services you required, ie: telnet 22, FTP 21, ssh 23, http 80 etc etc etc

I know that on my Linksys router I can have it tell DynDNS what my IP Address is through the web configuration editor - perhaps your old router has this, and your current one doesn't? Without some specifics your best bet is to play around untill you find exactly how you can and can't acces your server.

---

### Post by miss tina on 2005-07-04
give the no-ip duc a try
works for me and i'm behinde a router from d-link too
no-ip is in synaptic.... after install do no-ip -C to create the config
but first make an account at theire site it is free!

---

### Post by XoloX on 2005-07-24
Just today I've set-up ddclient to update my ip address once every day. Install it with "sudo apt-get install ddclient". It was configured to get the ip address from eth0, but that wasn't gonna do me any good since I'm behind a standalone (Belkin) router. To fix this, open "/etc/ddclient.conf" and change the "use=..." line to "use=web, web=checkip.dyndns.org/, web-skip='IP Address'". This fixed the problem for me :). Good luck

---

### Post by techflat on 2005-11-03
Thanx XoloX, it worked for me.

Still, does anybody know if there's a way to do it like this:
" use=dlink-614, fw=192.168.0.1 " ?

Or some other way? 

I'm using [www.zoneedit.com](www.zoneedit.com), I find it very good. Works fine for me.

---


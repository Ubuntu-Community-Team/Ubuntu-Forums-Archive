---
title: "ubuntu 10.04 LTS Tips for ferst time in my Dedicated Server"
date: 2011-05-29
forum: Server Platforms
---

### Post by thxyou on 2011-05-29
hello people i buy a Dedicated Server  ubuntu 10.04 LTS
and i  want use him just to host a game server (Counter Strike Source) 
this game server need port open (27015 UPD) help me how open it

and give me Tips about security and anti dos attacker

i start with this 
iptables -A INPUT -p udp --dport 27015 -m length --length 28 -j DROP

so i can start my work now and open my game server to people 

 i dont need any firewall or antivirus or what

pls give me just simple help

---

### Post by lisati on 2011-05-29
*Thread moved to **Server Platforms**.*
You might want to look into fail2ban, which monitors the system logs for suspicious behaviour and uses the iptables firewall to temporarily block badly behaving connections.

You might also want to look into mod_defensible, which can ban ip addresses based on rbl listings.

---

### Post by thxyou on 2011-05-29
> **lisati said:**
> *Thread moved to **Server Platforms**.*
You might want to look into fail2ban, which monitors the system logs for suspicious behaviour and uses the iptables firewall to temporarily block badly behaving connections.

You might also want to look into mod_defensible, which can ban ip addresses based on rbl listings.
I did not understand

---

### Post by lisati on 2011-06-09
> **thxyou said:**
> I did not understand

You asked for security tips for your dedicated server. fail2ban and mod_defensible are security tools that will help prevent people from misusing your server.

---

### Post by chazz_tsc on 2011-06-09
If you are connected to DSL or cable modem, and if you have more than one computer, you almost certainly have an external router box, as residential high speed access always seems to assume a single computer, unless they themselves provide you with a router box (many DSL suppliers will give you a 2Wire modem / router). If you have wireless, the wireless box is also a router. The router has to be told to accept connections on 27015 and route them to your server.

Unfortunately, we can't help with an external router, as every one is different... and the 2Wires often are locked down to the point that you can't open a port on them.

---


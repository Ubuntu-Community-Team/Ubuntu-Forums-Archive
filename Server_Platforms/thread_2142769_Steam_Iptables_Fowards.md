---
title: "Steam Iptables Fowards"
date: 2013-05-06
forum: Server Platforms
---

### Post by jamrop on 2013-05-06
Hey, I have my Ubuntu server routing all my internet traffic. I use iptables, and i am trying to get steam powered to work. I have tried opening the ports, but they do not seem to work. Just wondered if i am missing something,

Many thanks

iptables -I FORWARD 1 -p udp -m udp --dport 3478 --sport 3478  -j ACCEPT
iptables -I FORWARD 1 -p udp  -m udp --dport 27000:27015   -j ACCEPT
iptables -I FORWARD 1 -p udp -m udp --dport 27015:27030  -j ACCEPT
iptables -I FORWARD 1  -p tcp  -m tcp --dport 27014:27050  --sport 27014:27050 -j ACCEPT
iptables -I FORWARD 1 -p udp -m udp--dport 4380 --sport 4380  -j ACCEPT
iptables -I FORWARD 1 -p udp --sport 27000:27999 -j ACCEPT

Steam Client
UDP 27000 to 27015 inclusive (Game client traffic)
UDP 27015 to 27030 inclusive (Typically Matchmaking and HLTV)
TCP 27014 to 27050 inclusive (Steam downloads)
UDP 4380
 
Dedicated or Listen Servers
TCP 27015 (SRCDS Rcon port)

---

### Post by darkod on 2013-05-06
I don't understand. Where is the steam service running on? Another server?

---

### Post by d4m1r on 2013-05-09
Are you trying to setup servers for Steam games or are you just trying to run the Steam client locally? Are you connected to the internet behind a router and are you in control of it?

---

### Post by jamrop on 2013-05-11
Hey 

Setup

PC -- Ubuntu Server (with iptables) -- Router --Internet

No not trying to set up servers, just want to be able to connect to the stream service, but every time i load up stream, says unable to load, as no network connection. I have a router that i am in control of ,

---

### Post by darkod on 2013-05-11
I don't see much point having two routers in a row (router + ubuntu server acting as router), but it's your choice. Is forwarding enabled on the uubntu server in /etc/sysctl.conf?

Does the internet and pinging work and only the steam doesn't? Because all your routing might not be working on the server.

---

### Post by jamrop on 2013-05-11
Hey

Yes everything else works, just not steam :( yes forwarding is enabled. I have got e.g. irc to work fine, but just not steam

---

### Post by darkod on 2013-05-11
Do you know how that steam client works? Because I don't. Try to sit down and simply follow the traffic route.

Is the client (your PC) starting the connection or the destination steam server?

Try setting the FORWARD policy on ACCEPT temporarily and that will show you whether you have iptables problem or not.
If the connection is started by the server (which would be unlikely) you also need port forwarding (DNAT) from the external interface on the ubuntu server to the internal one. If your PC as a client is starting the connections, in that case the ACCEPT policy should be enough.
Also make sure you have a rule in FORWARD for established and related traffic. That is easy to miss, but necessary so that related traffic that comes back is handled correctly. With an ACCEPT policy you don't need this, otherwise it should be something like:
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

If port forwarding is needed it would look something like:
-t nat -A PREROUTING -i eth0 -p tcp --dport XXXX -j DNAT --to-destination 192.168.1.100

Depending how the traffic needs to "run", you might need to set port forwarding on your ubuntu server not only on the router. Because the way you explained it, the ubuntu server is your PC gateway in fact.

---

### Post by jamrop on 2013-05-12
Hey

I flushed my forward iptables rule, and it worked straight away

I changed the ports to what was put on port fowarding website Steam Client	TCP 27014-27050 	UDP 3478, 4379-4380, 27000-27030 

iptables -I FORWARD 1  -p udp -m udp --dport 3478 --sport 3478  -j ACCEPT
iptables -I FORWARD 1 -p udp  -m udp --dport 27000:27030 --sport 27000:27030  -j ACCEPT
iptables -I FORWARD 1 -p udp -m udp --dport 4379:4380 --sport 4379:4380  -j ACCEPT
iptables -I FORWARD 1  -p tcp  -m tcp --dport 27014:27050  --sport 27014:27050 -j ACCEPT
iptables -I FORWARD 1  -p udp  -m udp --dport 27015:27030  --sport 27015:27030 -j ACCEPT

but still not work.  Am i missing something or put something in wrong? many thanks

---

### Post by darkod on 2013-05-12
That is only rules for the forward chain. If you need port forwarding refer to the DNAT rule example I wrote above. But in that case it wouldn't have worked earlier after you flushed them.

The rules look good if those are the only rules you need. But obviously you need something more, either in the firewall or in the port forwarding on the ubuntu server (not the router).
Did you make sure you have the established and related rule for the forward chain too? I don't see it in the short extract you posted. Try adding this:
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

See if it works after that.

Also, I think you don't need the --sport option in the forward rules, maybe that's making the problem for you. You only need the --dport when the client tries to contact the server. Try it like that.

---

### Post by moody_mark on 2013-05-13
Doesn't steam use port 443 to authenticate? I'm pretty sure it does because I blocked port 443 for my kid's PC once before at the router and he couldn't login to steam, all other ports were open as I recall.

---

### Post by jamrop on 2013-06-02
still can not get it to work :(, I have port 443 open as well

---

### Post by Doug S on 2013-06-02
> **jamrop said:**
> I flushed my forward iptables rule, and it worked straight awayTo me, that does not make any sense, but if that works why not just leave it that way?

Please post your current iptables rule set, as it not clear to me from the thread what exactly it is at this point.

---

### Post by jamrop on 2013-06-02
Hey

I do not like to have my ports exposed, so I have the ports i need to be open and the rest closed


iptables -A FORWARD -i eth0 -o tap0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A FORWARD   -p udp  --dport 3478   -j ACCEPT
iptables -A FORWARD  -p udp  --dport 1200   -j ACCEPT
iptables -A FORWARD  -p udp  --dport 27000:27030   -j ACCEPT
iptables -A FORWARD  -p udp  --dport 4379:4380   -j ACCEPT
iptables -A FORWARD   -p tcp  --dport 27014:27050   -j ACCEPT
iptables -A FORWARD   -p udp   --dport 27015:27030   -j ACCEPT
iptables -A FORWARD  -p tcp --dport 4380  -j ACCEPT
iptables -A FORWARD  -p tcp  --dport 27000:27030   -j ACCEPT
iptables -A FORWARD  -p tcp  --dport 4379:4380   -j ACCEPT
iptables -A FORWARD   -p udp  --dport 27014:27050   -j ACCEPT
iptables -A FORWARD   -p tcp   --dport 27015:27030   -j ACCEPT
iptables -A FORWARD  -p tcp --dport 27000:27999 -j ACCEPT
iptables -A FORWARD  -p tcp --sport 5222 -j ACCEPT
iptables -A FORWARD  -p tcp --dport 5222 -j ACCEPT
iptables -A FORWARD  -p tcp --dport 6520:6540 -j ACCEPT
iptables -A FORWARD  -p tcp --sport 6520:6540 -j ACCEPT
iptables -A FORWARD  -p tcp --dport 6112 -j ACCEPT
iptables -A FORWARD  -p tcp --sport 6600 -j ACCEPT
iptables -A FORWARD   -p tcp --dport 993  -j ACCEPT
iptables -A FORWARD  -p tcp --sport 465 -j ACCEPT
iptables -A FORWARD  -p tcp --sport 6112 -j ACCEPT
iptables -A FORWARD  -p tcp --dport 6600 -j ACCEPT
iptables -A FORWARD -p tcp --dport 3128 -j ACCEPT
iptables -A FORWARD -p tcp --dport 563 -j ACCEPT
iptables -A FORWARD -p tcp --sport 563 -j ACCEPT
iptables -A FORWARD -p tcp --sport 3128 -j ACCEPT
iptables -A FORWARD  -p tcp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD  -p udp --dport 0:65535 --sport 53 -j ACCEPT
iptables -A FORWARD  -p tcp -m tcp --sport 80 -j ACCEPT 
iptables -A FORWARD -p tcp -m tcp --sport 443 -j ACCEPT 
iptables -I FORWARD -p tcp --dport 1194 -j ACCEPT
iptables -I FORWARD -p udp --dport 1194 -j ACCEPT
iptables -A FORWARD -i tap0 -j DROP

---

### Post by Doug S on 2013-06-02
> **jamrop said:**
> I do not like to have my ports exposed, so I have the ports i need to be open and the rest closedExposed to what? Your earlier posting said you have a router between your ubuntu server and internet.

I was hoping to see your entire iptables rule set, including default policies and such, not just a segment. Your FORWARD rules are somewhat disjointed and overlapping, adding to difficulties to understand what you are trying to do. Perhaps add a logging line before your tap0 general drop so you can observe what is being dropped to figure out what is missing. I'm saying this:```
iptables -A FORWARD -p tcp -m tcp --sport 443 -j ACCEPT
iptables -I FORWARD -p tcp --dport 1194 -j ACCEPT
iptables -I FORWARD -p udp --dport 1194 -j ACCEPT
[COLOR=#ff0000]iptables -A FORWARD -i tap0 -j LOG --log-prefix "Forward_tap0:" --log-level info[/COLOR]
iptables -A FORWARD -i tap0 -j DROP
```

---


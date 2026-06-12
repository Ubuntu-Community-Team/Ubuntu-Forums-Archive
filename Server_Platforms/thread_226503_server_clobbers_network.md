---
title: "server clobbers network"
date: 2006-07-31
forum: Server Platforms
---

### Post by bscook on 2006-07-31
hi:  just installed the ubuntu server LAMP to play around with.  the intention is to set it up to run sugarcrm.

everything installed just fine and even though i'm a linux newbie, it wasn't too hard to figure out.

however, right from the git-go, the server seems to periodically clobber the entire network.  i notice this when all the lights on my switch start to slow blink on/off simultaeously.  as soon as i unplug the server, everything comes back (except the server).  if i plug the server back into the network in a few minutes, it's fine too... until the next time.

if the server is mostly idle, then it won't crash the network, however if i use it for anything, it seems to setup to crash the network again in a few minutes.

i originally thought it might be a dhcp issue, so i set it for a fixed address by modifying /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.106
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

```

any ideas?

- bradley

---

### Post by verbatim210 on 2006-07-31
can you definate "crash" in more detail
i get the feeling its a client<ip>server problem
if your running dhcp the addresses shouldn't overlap
but the symptons sound suspiciously like ip conflict

incase your network setup is fine, suspect linux.
i had the same problem last night, had to restart the 
system a few times (uncessary because i dont know how 
to refresh an eth0 in linux)

restarted dhcp server, restarted linux fixed the ip
conflict problem and the network was running smoothly again

good luck

---

### Post by robert_pectol on 2006-08-01
You might want to install a packet sniffer such as tcpdump or ethereal, and have a look at your local network traffic.  It might clue you in to what's going on.

---

### Post by heisters on 2006-08-02
> (uncessary because i dont know how
to refresh an eth0 in linux)
```

# ifdown eth0
# ifup eth0

```
or, if you want to refresh all the networking mojo:
```

# invoke-rc.d networking restart

```

As for the OP.... I can't help much. Except to say, take a look on the server and see what's going on. Start with top for anything obvious, then take a look at tcpdump or ethereal as robert says. You also may not need to completely disconnect the server. Try just shutting down/restarting it's networking interface, similarly to how I just described (use "stop" instead of "restart")

---

### Post by verbatim210 on 2006-08-03
i actually tried that up/down eth command without achieving the results i expected.  this was a while ago so im not 100% clear on the details but i remember i had to use a more violent method like forcing a reboot or disconnect the cable.

off the top of my head, something like that.  are you definately sure up/down refreshs it like windows...

ipconfig /release
ipconfig /renew?

---

### Post by bscook on 2006-08-09
okay, thanx for the feedback all.  i originally suspected dhcp prob's so i turned off dhcp for the network and gave everything a fixed address.  makes no difference.  i've got two ubuntu systems on my network and several windows machines.  one of the ubuntu systems has the desktop which i just installed on my computer and i've installed the lamp on an old p3 to play around.  to be honest, i can't tell what starts the problem... the only solution is to unplug the server from the network.  
by crash i mean that the entire network becomes unusable, regardless of system subnet etc.  the first hint is when i experience long delays.  i can confirm the error condition by looking at one of the switches and observing all leds on all ports slow blinking in unison.  by disconnecting the lamp server, everything else comes back up instantly.

---


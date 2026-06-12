---
title: "Firewall help - I am noob, please bear with me"
date: 2013-05-12
forum: Security
---

### Post by bzKniGhtz on 2013-05-12
I read about shorewall. Are there any other firewall available for me to choose from? If yes, what firewall is recommended?

---

### Post by The Cog on 2013-05-12
I believe that ufw is the recommended firewall for Ubuntu. In general, all you need to do is run the command
```
sudo ufw enable
```
and this will give you all the firewalling most people need - allow all outgoing connections but block all incoming connections.

---

### Post by bzKniGhtz on 2013-05-12
thank you very much for the prompt reply

---

### Post by Koori23 on 2013-05-15
I tend to be a bit picky, so this is how I check to make sure everything is good..

Once your firewall is enabled. Run the following command

sudo ufw status verbose

You should see output similar to this:

[I]Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip[/I]

---

### Post by kleenex on 2013-05-17
There is one more method to create a very good firewall for Desktop:

```
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo touch /etc/init.d/iptables[/COLOR]  # create a file for rules
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo leafpad /etc/init.d/iptables[/COLOR]  # edit file with 'leafpad', 'gedit' or 'medit' etc.

```

Add this lines to the [COLOR=#008000]/etc/init.d/iptables[/COLOR] file (e.g. copy and paste) and save changes

```
#!/bin/bash

echo "Starting Firewall"

iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

iptables -A INPUT -i lo -j ACCEPT

iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
```
  
Now, let's set the firewall to start every time, on boot

```
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo chmod +x /etc/init.d/iptables[/COLOR]  # make file executable
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo update-rc.d iptables defaults [/COLOR] # install System-V style init script links for iptables
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo /etc/init.d/iptables[/COLOR] [enter]  # start firewall
[COLOR=#008000]Starting Firewall[/COLOR]
[COLOR=#ff0000]$[/COLOR] [COLOR=#008000]sudo iptables -L -n[/COLOR]  # check filter status
```

That's all. Of course everything mentioned above is also good.

---

### Post by deadflowr on 2013-05-17
> **The Cog said:**
> I believe that ufw is the recommended firewall for Ubuntu. In general, all you need to do is run the command
```
sudo ufw enable
```
and this will give you all the firewalling most people need - allow all outgoing connections but block all incoming connections.

ufw is installed but not enabled by default.
Rather simple to get setup.
```
man ufw
```

Will give you the manual for it.

The default enabled settings are deny in , allow out.
Tweak to your own delight.

---

### Post by kevdog on 2013-05-18
Look, your basically going to get two opinions to your problem.

A lot of people in these forums don't use shorewall, so your not going to get a lot of help from that aspect.

The other most commonly used Ubuntu firewalls are ufw (or gufw if you want a gui interface to ufw) and iptables.  ufw is a frontend to iptables, so its usually easier to use for basic things since "its a frontend".  Depending on what you need to use your firewall for, you may or may not prefer ufw compared to iptables.  

Any firewall is kind of a pain to use -- meaning you aint going to master firewall construction in like 15 minutes.  You need to know basics about tcp and udp packets and how they are routed (through what chains) in order to make a decent firewall. This unfortunately means you're liking going to have to make a small commitment to reading and trying things out, and become very knowledgeable about how to interpret log files so you know if you're firewall is actually blocking packets you want to drop.  I'm still learning a lot about iptables after several years.

---

### Post by kleenex on 2013-05-18
Hi, **kevdog** You are right. A lot of people in these forums don't use shorewall, so the best choice is UFW (GUFW) or iptables. Firewall proposed in my post #5 is pretty good and secure. All incoming connections are blocked (DROP) and only established and related connections started by user are allowed. In my opinion this is sufficient configuration for desktop - without any running services, such as ssh, Samba etc. To create more "hardened" firewall you can add to the iptables script something like this;

```
[B]# every new connection attempt should begin with a syn packet  
# if it doesn't, it is likely a port scan.[/B]
iptables -A INPUT -p tcp ! --syn -m conntrack --ctstate NEW -j LOG --log-level debug --log-prefix "ScanAttempts: "
iptables -A INPUT -p tcp ! --syn -m conntrack --ctstate NEW -j DROP

**# and maybe something for bad tcp packets and for hindering port scanners**
iptables -A INPUT -p tcp --tcp-flags SYN,ACK SYN,ACK -m state --state NEW -j REJECT --reject-with tcp-reset
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH ACK -j DROP
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH FIN -j DROP
iptables -A INPUT -m conntrack --ctstate NEW -p tcp --tcp-flags SYN,RST,ACK,FIN,URG,PSH FIN,URG,PSH -j DROP

**# you can also DROP icmp packets: echo-request**
iptables -A INPUT -p icmp -j DROP
iptables -A INPUT -p icmp --icmp-type echo-request -j DROP

```

Please remember, that it is only examples! I wrote it quickly so something may be wrong with these rules - I did not use iptables for a long time. Oh, by the way; all logged events you can find in [COLOR=#008000]/var/log/kern.log[/COLOR] or [COLOR=#008000]/var/log/syslog[/COLOR] files (first rule for connections without syn packets).

---

### Post by HermanAB on 2013-05-18
Howdy,

I used shorewall many moons ago.  If it is anything like it was then, then it provides a ton of filter rules against a ton of things are never going to happen on a LAN and protects you against a bevy of network stack problems that do not exist anymore...

When I run a server on the internet, I use only a rate limit rule.  Nothing else.  My servers typically stay up until the PSU fails in 4 to 5 years.

On my home machines I use nothing, since they are behind a dinky little NAT router.  A typical home router is so slow, that nothing of consequence will get through.

On my laptop machines that get carried around the world and plugged into strange nets, I use the same rate limiting rule as on the servers.

So, before you go totally crazy with firewalls, have a good think about what you are trying to achieve.

---


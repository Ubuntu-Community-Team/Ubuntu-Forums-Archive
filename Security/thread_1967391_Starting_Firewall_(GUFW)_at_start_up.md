---
title: "Starting Firewall (GUFW) at start up?"
date: 2012-04-28
forum: Security
---

### Post by OpenSourceRules on 2012-04-28
I add it to start up, but it is disabled; how may I make it starting up at boot?

---

### Post by Blackbird_13 on 2012-04-28
No need to add to startup.

Open GUFW and tick "enable".

Or open a terminal:
```
sudo ufw enable && sudo ufw status
```

---

### Post by HermanAB on 2012-04-28
Hmmm, why do you think that you need to run a firewall?  A firewall is mostly a Windows thing - it is a band aid that you have to add when a server is not under control and cannot be trusted.  A normal Linux desktop system doesn't need one and if you run a server then you should know what you are doing and also should not need one.

---

### Post by Ms. Daisy on 2012-04-28
> **HermanAB said:**
> Hmmm, why do you think that you need to run a firewall?  A firewall is mostly a Windows thing - it is a band aid that you have to add when a server is not under control and cannot be trusted.  A normal Linux desktop system doesn't need one and if you run a server then you should know what you are doing and also should not need one.
Wow. I'm not sure where to start with that.  Why would you not run a firewall on a Linux server?  How is that good advice?  Surely you're trolling?

Here's a link that would be excellent reading for you:

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by Soul-Sing on 2012-04-30
HermanAB is not a person to troll around on this forum. :)

---

### Post by Morbius1 on 2012-04-30
Um ....

There already is a mechanism in place that starts automatically when you boot that handles the "firewall" by default. 

Something called iptables contains the rules that the "firewall" uses.

ufw is a command line tool to set those rules.

gufw is a graphical front end to ufw.

Once you use gufw to set or modify a rule you no longer have to have it running.

---

### Post by Soul-Sing on 2012-04-30
netstat/filter is dead on a clean install. or am I missing your point?
[COLOR="Red"]netstat--(iptables--ufw/gufw)[/COLOR]
the syntax of ufw is somewhat similar to the iptables syntax.
but wthout "rules" netstat is disabled.

the "zero open ports policy" one. or the "no sign. services are listening" one. 
whats the point using a firewall when your op-system has its ports closed?
imho you have to disable:
- avahi
- geo-ip
- maybe dnsmasq (on localhost level)
- amazon web (when using ubuntu-one)
to get your system not responding to the outside world.( ubuntu 12.04)
closing all "listening services", or not used services, does harden your system, and no active additional firewall is needed.

---


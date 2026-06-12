---
title: "iptables like freebsd PF"
date: 2007-12-27
forum: Server Platforms
---

### Post by ottothecow on 2007-12-27
I've got a box running ubuntu-server (gutsy) and I've got a firewall question.

On a base FreeBSD install I can
put pf_enable="YES" in /etc/rc.conf
to turn on packetfilter

Is there any way to easily get the equivalent protection using iptables on ubuntu?  Just a similar set of rules to whatever pf_enable="YES" would turn on to automatically start and protect my ubuntu box?

Thanks

---

### Post by p_quarles on 2007-12-27
Having not used FreeBSD PF, I don't really have any basis for comparison, but there are several iptables configuration utilities that aim to simplify the process of settings things up.

Command line:
Shorewall
Firehol

Graphical:
Firestarter
Guarddog
fwbuilder

---

### Post by cdenley on 2007-12-28
iptables is enabled by default, but configured to accept everything. It's been a while since I used FreeBSD, but I think if you don't configure the firewall script after you enable packet filtering, it blocks everything by default. There is no standard firewall script like /etc/rc.firewall, but you can make one for iptables, then execute it on startup by adding it to /etc/rc.local. However, it would be much easier to use one of the tools already mentioned.

If you want iptables to block everything:
```

sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT DROP

```

---

### Post by p_quarles on 2007-12-28
That will certainly block everything, including all outbound network connections. You could accomplish the same thing by simply unplugging the computer from the network. 

That said, something very similar to that could work, if you only needed a few very specific services. The iptables configuration on my server, in fact, works just like that: the POLICY setting for all tables is DROP, but I have a few rules that allow the services I want. 

If you want to do that, or if you find a set of pre-written iptables rules that you want to use, it's pretty easy to turn it into a startup task. I use a slightly different method than cdenley, though. In /etc/network/interfaces, I add the following line directly below the entry for the main network device:
```
pre-up iptables-restore < /etc/iptables.up.rules
```
Then, I save the iptables rules I want to the file called /etc/iptables.up.rules . Those rules will now initialize when the network device does.

If you use a script to create the iptables rules, you'll need to use a different method to save those rules to the file:
```
sudo sh -c "iptables-save > /etc/iptables.up.rules"
```

---


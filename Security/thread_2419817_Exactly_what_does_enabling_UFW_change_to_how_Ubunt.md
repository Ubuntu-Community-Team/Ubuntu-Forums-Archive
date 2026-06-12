---
title: "Exactly what does enabling UFW change to how Ubuntu 19.04 handles network connections"
date: 2019-05-25
forum: Security
---

### Post by Mr. Swiveller on 2019-05-25
I am afraid that this is another 'firewall post'. Although my Ubuntu account is quite old, I was a heavy Windows user until quite recently, and so I find that, at times, my knowledge is still lacking.

Recently, I have been trying to figure out what exactly would change if I were to enable UFW. It is my understanding that UFW is a means to set and modify iptables rules. I have used GUFW in the past, however, and remember that it features an on/off switch for the Ubuntu firewall. I would not expect this to be the case if all UFW did was allow the user to modify the rules governing network traffic (and not, therefore, the system applying those rules). 

Could someone please tell me which of the following two applies?

a) Without UFW Ubuntu does **not** use a firewall.
b) Without UFW Ubuntu **does** use a firewall, but UFW adds a switch which allows the user to disable it.

If (a) applies: how does network security work on Ubuntu if, by default, there is no firewall? UFW is currently inactive on my system (I checked using the command **sudo ufw status verbose**), yet when I go the Gibson Research 'Shields Up' service, it shows that all of the ports on my PC are stealthed.

If (b) applies: would enabling UFW, and thus adding an on/off switch for the firewall, not represent a security risk in and by itself? Also, I wonder if UFW, by applying its default rules, might open ports that would otherwise remain closed?

I have tried to find answers to these questions, yet the information that I have so far come across has left me confused:

* One post claimed that the firewall '[was running by default]("https://askubuntu.com/questions/9206/is-there-a-preinstalled-or-automatic-firewall")'. 
* Other posts suggested that Ubuntu [did not need a firewall]("https://ubuntuforums.org/showthread.php?t=1714727") since vulnerable ports were closed anyway.
* Yet other posts said that one should [enable the firewall to be on the safe side]("https://askubuntu.com/questions/22667/why-is-the-firewall-disabled-by-default"). 

Many thanks in advance!

---

### Post by ajgreeny on 2019-05-25
Not a simple question to answer, I'm afraid, but have a look at the security wiki for Ubuntu at [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) where you can see all (and more) that you need to know.

You can go to the link for UFW on that page and you will get everything about firewalls and how to configure them. Truth to say, I have been using desktop Xubuntu now for 15 years and never needed to enable the firewall using UFW or anything else.  If you are using a standard desktop machine rather than a server, you may also not need to enable the filrwall.

It is also worth mentioning that UFW is not actually the firewall, it is simply a command line configuration utility for it.

---

### Post by Mr. Swiveller on 2019-05-26
Thank you for your reply.

I am afraid that the Ubuntu documentation pages on security do not help much, however.

The page on UFW states that 'ufw provides a user friendly way to create an IPv4 or IPv6 host-based firewall'. And that 'by default UFW is disabled'. 

This would imply that no firewall is running without UFW, as apparently a firewall must be 'created'. Is this true though? As the page explains, when the default UFW settings are applied "all 'incoming' is being denied". But is this not what normally happens on Ubuntu, whether or not UFW has been 'enabled'? 

All in all, am I correct in assuming that Ubuntu actually does apply certain netfilter settings which could collectively be descrided as a 'Firewall', and that UFW allows the user to change those settings? And, if so, what does setting the firewall to 'off' in UFW actually do? Disable all net filtering, or simply revert settings to Ubuntu defaults?

---

### Post by kpatz on 2019-05-26
ufw is an interface to iptables, which in turn is an interface to netfilter.  Netfilter is part of the kernel and provides the actual "firewall".

Technically there is always a "firewall" but the default configuration is wide open, no filtering.  Once you use iptables (or ufw) to add rules to netfilter, they are applied immediately.

When you add rules to ufw, they are stored in ufw.  When you apply the firewall (or enable it) in ufw, it creates the rules in netfilter.  When you disable ufw, it deletes the rules and resets the default policies, but ufw keeps the rules stored in its own database, so they can be re-enabled again.  ufw also handles reapplying the rules after a reboot... iptables/netfilter has no persistence across reboots, so a script has to reapply them after a reboot.  ufw handles this for you.

To see how this works, use the command **sudo iptables -L -n** to view the netfilter rules as you set them up in ufw.  If ufw is disabled, you won't see any changes in the output of iptables until you enable ufw.

---

### Post by maglin2 on 2019-05-26
> **kpatz said:**
> ufw is an interface to iptables, which in turn is an interface to netfilter.  Netfilter is part of the kernel and provides the actual "firewall".

Technically there is always a "firewall" but the default configuration is wide open, no filtering.  Once you use iptables (or ufw) to add rules to netfilter, they are applied immediately.

When you add rules to ufw, they are stored in ufw.  When you apply the firewall (or enable it) in ufw, it creates the rules in netfilter.  When you disable ufw, it deletes the rules and resets the default policies, but ufw keeps the rules stored in its own database, so they can be re-enabled again.  ufw also handles reapplying the rules after a reboot... iptables/netfilter has no persistence across reboots, so a script has to reapply them after a reboot.  ufw handles this for you.

To see how this works, use the command **sudo iptables -L -n** to view the netfilter rules as you set them up in ufw.  If ufw is disabled, you won't see any changes in the output of iptables until you enable ufw.

I can't comment on the accuracy of this, but for succinctness and clarity I think it's great.

---

### Post by Mr. Swiveller on 2019-05-26
> **kpatz said:**
> ufw is an interface to iptables, which in turn is an interface to netfilter.  Netfilter is part of the kernel and provides the actual "firewall".

Technically there is always a "firewall" but the default configuration is wide open, no filtering.  Once you use iptables (or ufw) to add rules to netfilter, they are applied immediately.

When you add rules to ufw, they are stored in ufw.  When you apply the firewall (or enable it) in ufw, it creates the rules in netfilter.  When you disable ufw, it deletes the rules and resets the default policies, but ufw keeps the rules stored in its own database, so they can be re-enabled again.  ufw also handles reapplying the rules after a reboot... iptables/netfilter has no persistence across reboots, so a script has to reapply them after a reboot.  ufw handles this for you.

To see how this works, use the command **sudo iptables -L -n** to view the netfilter rules as you set them up in ufw.  If ufw is disabled, you won't see any changes in the output of iptables until you enable ufw.

Ah, thanks - this is very helpful!

This does make me wonder why the default rules applied by UFW are not enabled by default. Does anyone know?

---

### Post by deadflowr on 2019-05-26
The defaults of off is because it's unknown what the machine would be used for.
If using a desktop or even a server and you plan on file sharing you need to open one port, if using it for something like a webserver you need another and so on.
The distribution cannot guess what the machine will be used for.

And there is no way for them to know if you run various services through non-default ports either.
(People do this regularly with ssh where they change the default port to some other port, as an example)

So it's easier just to set it to off for starters and let the machine's system admins control it from there.

---

### Post by kevhilton on 2019-05-26
I don't think there are any default UFW that I know -- all incoming ports are closed to my knowledge although I'm not sure of icmp (which is the ping protocol). UFW is good for a single end computer, but I don't think you can configure forwarding through it if your computer is acting as a gateway or router.  I know this is a little off topic, however I used iptables (and rarely UFW) for years.  I gained a lot of knowledge, however it was always more cumbersome each time I bought a new computer I had to set everything back up again for the different machine.  I eventually built my own router from scratch and installed pfSense.  I'm aware pfSense is freeBSD based however the firewall and routing concepts are very similar to iptables.  In general I've learned its just much easier configuring filtering rules at the router level than the individual level -- there is possible a place for both given the fact security is a multilayered process -- however its also easier to manage at the firewall level.

---

### Post by Mr. Swiveller on 2019-05-27
Thank you both!

---

### Post by DuckHook on 2019-05-27
Might I add my belated two bits?

Conceptually, a firewall is not an app. It is a set of rules that tell your machine which packets are permitted to access your machine and which are not, where packets should be routed, how they should be filtered/forwarded, etc.

Ubuntu comes with the building blocks for a firewall already built-in. However, these are just building blocks. Without a set of rules, it's not a firewall.

It also comes in a default state wherein all ports are closed. A lot of people mistaken this for a "firewall". But it is not. It is simply a middlingly secure default state. If, for example, a rogue app opens a port, there are no rules in place preventing that port from opening. Therefore, until you define that set of rules, you don't have a firewall.

Moreover, a firewall isn't simply a firewall. There are good firewalls and bad firewalls. A good set of rules will give you a good firewall. A bad set will yield a bad firewall. A really bad set is equivalent to no firewall at all. Our long-time forum member, TheFu, is always very concerned to advise people to set up vigorous outgoing port restrictions; not just incoming. This is to prevent rogue apps or javascripts from opening ports to communicate with command-and-control servers.

UFW is nothing more than a rules builder. It must be set up properly with a good set of rules or else it is just a worthless app. No one can set UFW up for you, because we have no idea what you use your computer for. It's one of those important chores that one must do and continue to maintain as one's computing needs change. If you start using ssh? You must open a port. VPN? Open a port. Etc. Otherwise, all ports closed, both incoming and outgoing.

Hope this helps.

---

### Post by Mr. Swiveller on 2019-05-31
Thank you for your response.

For now, I have blocked all of the incoming connections. I may eventually block the outgoing connections too, yet since I rarely install anything other than software from the repositories I will keep things the way they are for now.

---


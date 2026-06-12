---
title: "Shields up - A Query"
date: 2006-02-27
forum: Server Platforms
---

### Post by Strev_123 on 2006-02-27
Dunno if this has any relevance to Linux or whether it's windows specific, I assume it does 'cos it scans service ports, but hey, I'm new to this. When scanning all the service ports 0-1055 they are all returned as stealth, but my system fails because apparently it has returned a Ping (ICMP Echo) request which makes it visible to scans. Is this of any importance and how can I block them. I dual boot with Win2000 and using Zonealarm Pro my system passes all the tests and returns nothing what so ever.

Thx in advance \\:D/

---

### Post by az on 2006-02-27
You can tell your box to not respond to pings, and you can also firewall your box up the wazoo.  It doesn't matter.  The minute you visit a website, the webserver you are visiting knows you are there, whether you answer pings or not.

It is irrelevant.  For the most part, firewalls on linux desktops are irrelevant - just don't run anything that listens to the outside world.  You (in general) don't have the control to do that on a windows machine.

---

### Post by Rizado on 2006-02-28
Although a firewall is highly recommended. It's actually in the kernel and is called iptables. All "firewalls" in linux is actually just tools that tell iptables what to do. Iptables by the way is really hard to configure not using any tools.

Firestarter is really easy to use and great if your computer is connected directly to the internet and you only need to do the normal tasks (stealthing you computer, open some ports) If you want to do more things like masquerade and sharing and so on go for something more advanced, like firehol.

---

### Post by dbee on 2006-03-02
Shields up is probably more relevant for a windows box than it is for a linux one. Since they both have different security architecture

---

### Post by nocturn on 2006-03-02
[QUOTE=Strev_123]Dunno if this has any relevance to Linux or whether it's windows specific, I assume it does 'cos it scans service ports, but hey, I'm new to this. When scanning all the service ports 0-1055 they are all returned as stealth, but my system fails because apparently it has returned a Ping (ICMP Echo) request which makes it visible to scans. Is this of any importance and how can I block them. I dual boot with Win2000 and using Zonealarm Pro my system passes all the tests and returns nothing what so ever.

Thx in advance \\:D/[/QUOTE]

If you really want to turn ICMP packages of, install and run firestarter, it has an option for it.

---

### Post by nocturn on 2006-03-02
[QUOTE=dbee]Shields up is probably more relevant for a windows box than it is for a linux one. Since they both have different security architecture[/QUOTE]

They are different, but stuff like shields up works equally well against both.

It just scans for open ports on your system and replies to ICMP packets.

Actually, the Microsoft TCP/IP stack is very similar to the one in Linux because it's a rip from the BSD one (allowed under the BSD license).  The main difference is that a default XP install has way to many services listening.

---

### Post by az on 2006-03-02
Use 
netstat --tcp -anp
to see what you have listening.

---

### Post by imagine on 2006-03-02
[QUOTE=Strev_123]Dunno if this has any relevance to Linux or whether it's windows specific[/QUOTE]
IMHO Shields Up! isn't relevant to any operating system.

[QUOTE=Strev_123]but my system fails because apparently it has returned a Ping (ICMP Echo) request which makes it visible to scans. Is this of any importance[/QUOTE]
No.
Check this thread: [http://ubuntuforums.org/showthread.php?t=117123](http://ubuntuforums.org/showthread.php?t=117123)

Moreover, if you didn't install any services on your system, you don't have to bother about a personal firewall.

---


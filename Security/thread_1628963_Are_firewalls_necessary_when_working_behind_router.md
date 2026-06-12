---
title: "Are firewalls necessary when working behind routers?"
date: 2010-11-23
forum: Security
---

### Post by Emporata on 2010-11-23
I used to think that they were always necessary--but what do I know?  I just installed the latest distro of Ubuntu on a computer which is behind a router and, based on some comments I have read recently, I was wondering if it should be firewalled?  Also, if I should firewall it, which is the easiest firewall application to use?

Thanks very much!

---

### Post by Sylos on 2010-11-23
Hello there.

Im not going to get into the debate over whether it is necessary or not (i dont really know enough about it to comment). However, should you choose to install one I can recomend Firestarter (available in repos). This is just a front end for IPTables (as most of the other firewalls you'll find are). It's quite easy to set up and from what I have read is quite effective.

---

### Post by Drenriza on 2010-11-23
I would say it depends on your router. Since the routers more and more will be the frontline in firewalling.

I would not use a firewall when using cisco catalyst routers. ACL (access control list) i can setup. To minimize "internet dangers" and then i guess a good anti virus / anti malware would kill off anything else.

And fore the record i dont use firewalls in my home network, since i have setup my routers to minimize unwanted traffic. And in my network they do more harm than good.

---

### Post by Emporata on 2010-11-23
Thanks everyone.  

I called my ISP.  Happily, they recently sold me a modem-router combo and it is firewalled.

---

### Post by magnatron on 2010-11-23
Even with a hardware firewall you will still get traffic in some form or another, I find the most common types are UDP with DF flags. the DF flags mean don't fragment but if you hose any open services and turn all your ports with listening services off, those packets are automatically dropped by the kernel.

---

### Post by endotherm on 2010-11-23
the only times you need a firewall when you already have a router firewall are:
1) you wish to filter outbound traffic
2) you have a net app that you wish to make available to some people within your network, but not to others
3) you have a direct connection to the internet. 
4) you have for some reason opened up a significant whole in your router's firewall, and need to mitigate that risk.

---

### Post by SebastianG63 on 2010-11-24
As long as you have any ports available seen from outside, you should have some mechanics handling attempts to gain control over your system. A firewall will handle some of them, but some it will not at all.
A regular request to your e.g. Apache- or NTP-server, if you have running any such, might still offer chances for a potential attacker in long term by brute force/zero exploits mechanics.
So it's propperbly a good choice to have some scripts/service running, beside firewalls, that take a deeper look into your service-logs generated from your public services and drive 'iptables' or at least '/etc/deny.hosts' from it's observations from the logs.
Some of the 'almost normal' looking activities could compromise a system one day.

So never turn off deepest possible logging for your public services, even with your hands on the best firewall ever, and take time to inspect your logs as well manually on a regular base!

So to say, whenever you have a server running all time, you might possibly want to put some more effort into it, than setting up a firewall once and forget; else you perhaps might regret after some time.

---

### Post by bodhi.zazen on 2010-11-25
It depends on two things:

1. What services, if any you are running. If you are running a service, such as ssh, apache, ftp, VNC, etc you need to learn to secure them. A firewall can help, but if you are running a public service, such as Apache, then a firewall is less helpful.

You could look at tools such as snort to monitor netowrk traffic, fail3ban, denyhosts etc. See the stickies.

Personally I prefer not to install additional services, I configure iptables directly, although that also varies some what by server and service (and who is going to monitor it).

2. It also depends on your LAN. If you trust all your clients, then no need for a firewall on the clients. This is typically the case on a Home or small office.

But if you are on an untrusted network, such as a public wireless network, and you are running services, then a firewall makes sense.

So you need to understand your network and the threats.

---

### Post by CharlesA on 2010-11-25
bodhi covered it.

My main server is firewalled, but the ones I use only internally aren't.

I mostly use the other servers for dev work (as they are virtual machines) and don't access them from the internet directly.

---

### Post by SebastianG63 on 2010-11-25
It's pretty important to understand, that firewalls block/allow traffic for some specific addresses(machines), ports and protocols. And no more!

What a firewall does not do, is to understand the content in packets and their purpose within the designated facilities.

In example, a tcp-packet for apache can contain a request for sending content of a certain url. But on a Zero-Day it perhaps will contain an exploit instead?! A firewall does not understand anything of both the cases. [COLOR=Black]Same thing along with other services like [/COLOR][COLOR=Black]ftpd / [/COLOR][COLOR=Black]sshd / ntpd / mysqld and so on…
[/COLOR]
Firewalls are very good to block the "bad guys" (blacklist) and only allow things for the good ones (white list). But since even zero-day-exploits mostly do not allow a simple '*walking through the main entrance*', logs mostly show certain types of atempts in advance when people start attacking a machine to *somehow* get their exploit working.

Observing logs plays, besides a firewall, an important role in prophylactic security!

The best choice is to have a firewall, but not in terms of "install and forget", and additionally examine log files or make use of tools that do so in a more automated fashion. 
Logs can also make a good source for specifying additional firewall rules. So it's worth looking at them from time to time… ;)

---

### Post by bodhi.zazen on 2010-11-25
> **SebastianG63 said:**
> Observing logs plays, besides a firewall, an important role in prophylactic security!

"Observing logs" is extremely time consuming and on a busy server looking for problematic packets or sifting through the apache logs is akin to looking for a needle in a haystack. Even the ssh logs can be large fast.

Again, it depends on the service, but this is what snort is for. Snort examines your traffic and alerts you to problematic packets. Snort generates a lot of false positives, but al least you now can go through a list of 100 or so potential problems rather then 10,000,000 packets, the majority of which are normal traffic.

Another helpful tool, at least IMHO, is OSSEC.

---


---
title: "Snort Network Hardware Configuration Advice"
date: 2009-04-24
forum: Server Platforms
---

### Post by Dogmatix86 on 2009-04-24
Hi There,
 
I'm running Ubuntu Server 8.04 LTS Server Edition and I'm in the process of putting together a server running Dansguardian, Squid, Shorewall, Snort and some other bits and peaces.
 
I'm looking for advice on good networking hardware configurations. 
 
I have three ethernet cards (bought two gigabit nics plus there is an onboard) with 4GB RAM. The CPU is an AMD Athlon X2.
 
I would like the box to dialup the dsl connection for the network.
 
I read in this howto: (Part 3) [http://www.enterprisenetworkingplanet.com/reports/article.php/3749386/Run-a-Business-Network-on-Linux-Intrusion-Detection-Part-3.htm](http://www.enterprisenetworkingplanet.com/reports/article.php/3749386/Run-a-Business-Network-on-Linux-Intrusion-Detection-Part-3.htm)
(Part 4 if you are interested) [http://www.enterprisenetworkingplanet.com/reports/article.php/3751796/Run-a-Business-Network-on-Linux-Intrusion-Detection-Part-4.htm](http://www.enterprisenetworkingplanet.com/reports/article.php/3751796/Run-a-Business-Network-on-Linux-Intrusion-Detection-Part-4.htm) that it's good practice to put one of your NICS (preferably eth0) in promiscuous mode and use another NIC to manage the box by doing the following:
 
[FONT=Courier New]# The loopback network interface[/FONT]
[FONT=Courier New]auto lo[/FONT]
[FONT=Courier New]iface lo inet loopback[/FONT]
[FONT=Courier New] [/FONT]
[FONT=Courier New]# Snort's stealth listening interface[/FONT]
[FONT=Courier New]auto eth0[/FONT]
[FONT=Courier New]iface eth0 inet manual[/FONT]
[INDENT][FONT=Courier New]up ifconfig eth0 0.0.0.0 up[/FONT]
[FONT=Courier New]up ip link set eth0 promisc on[/FONT]
[FONT=Courier New]down ip link set eht0 promisc off[/FONT]
[FONT=Courier New]down ifconfig eth0 down[/FONT]
[FONT=Courier New] [/FONT]
[/INDENT][FONT=Courier New]# Management Interface[/FONT]
[FONT=Courier New]auto eth1[/FONT]
[FONT=Courier New]iface eth1 inet dhcp[/FONT]
 
[FONT=Verdana]Is this good practice?[/FONT][FONT=Verdana]Also, is it better to have Snort sniff your LAN or your WAN interface (in my case ppp0) and why?[/FONT][FONT=Verdana]I can't get my head around intrusion detection sniffing around your local network when the intrusions come from outside? Yes I know...i'm a noob :P[/FONT]
 
[FONT=Verdana]Thanks in advance, Dogmatix.[/FONT]

---

### Post by mrsteveman1 on 2009-04-24
What you appear to want is an all-in-one box with snort in inline mode rather than passively collecting traffic, so that you place the snort box inline between the DSL connection, and your network.

However, the snort configuration described there is actually the sort you would use if you wanted to monitor an entire network passively, without the snort box actually being involved in routing traffic. Usually in that case, you use a special switch port to forward all traffic to this snort box because otherwise the switch will only forward traffic destined for the mac address of the NIC (this is why you set promisc mode too, so it can see all traffic). As i say, this is probably not what you want.

Are you planning on also running other services on this server like apache, or is this just going to be a networking device? I usually keep network functions like snort, firewall and content filtering separate from services like apache.

I also tend to shy away from configuring things like this by hand, in part because it requires a fair amount of work, and because there are premade linux distributions that can do it all for you and are intended for this purpose. Most of them have nice management interfaces too. I've personally used Smoothwall, Astaro security gateway and pfSense (this one is actually freebsd not linux). All are free (astaro free for small networks), all are easy to work with and support all the things you listed in your post.


[http://www.astaro.com/our_products/astaro_security_gateway]("http://www.astaro.com/our_products/astaro_security_gateway")

[http://www.smoothwall.org/]("http://www.smoothwall.org/")

[http://www.pfsense.com/]("http://www.pfsense.com/")

---

### Post by Dogmatix86 on 2009-04-24
Hi!

I have used IPcop, pfSense & Untangle so far. All of which have a few things that I really like and things I don't. Which is why I have decided to build my own.

Reporting is quite important to me so for the purposes of BASE and other reporting software, I would need apache and mysql installed on the same box. I am aware of the security implications involved and will deal them accordingly.

Can snort in inline mode work with ppp connections?

---

### Post by mrsteveman1 on 2009-04-24
> **Dogmatix86 said:**
> Hi!

I have used IPcop, pfSense & Untangle so far. All of which have a few things that I really like and things I don't. Which is why I have decided to build my own.

Reporting is quite important to me so for the purposes of BASE and other reporting software, I would need apache and mysql installed on the same box. I am aware of the security implications involved and will deal them accordingly.

Astaro has very good reporting capabilities, its an enterprise network appliance.

> Can snort in inline mode work with ppp connections?

Sure, snort is only concerned with network traffic, as long as something presents an interface to the OS it will work

---


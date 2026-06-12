---
title: "Turning an old pc into a firewall/proxy"
date: 2009-02-05
forum: Security
---

### Post by RFXCasey on 2009-02-05
I have started accumulating quite a few computers on my home network and to simplify my life I want to turn an old pc into a dedicated firewall. I've read a bit on the subject already but I have a few questions the hopefully someone can help me to clarify. First off what is currently the best software to use? I have read pretty good things about smoothwall and devil linux. I am by no means a linux expert so keeping things as easy to setup and manage as possible is a concern. I also was wondering about setting up a webfilter that will trickel down to all the machines on my network. I guess this would be a proxy I am talking about. Does smoothwall or devil come with one built in? And if I use one of those distros, would I also be able to use the firewall as a print server? Lastly what would you say is the minimum system requirements you would recommend if I wanted stateful packet inspection on a network of no more then 10 machines with only 3 or 4 running at any given time?

---

### Post by Dr Small on 2009-02-05
To use a a system as a firewall, you'll need to NICs. One for input, one for output and the firewall sits in the middle doing all the routing.

For web filtering, you setup the web filter on the firewall box and set some firewall rules to redirect traffic through the web filter. So it will look like this:

LAN --> FW BOX [IN] --> [iptables -> DansGuardian -> Squid] -> FW BOX [OUT] --> MODEM

---

### Post by RFXCasey on 2009-02-07
Well, while I appreciate the replay, it really doesn't answer any of the questions I asked. I already have a pretty firm grasp on what you are talking about.

---

### Post by koenn on 2009-02-08
you'll need iptables to do the packet filtering. It also does NAT/masquerading to implement internet connection sharing.
routing will be handled by the kernel automatically in most common cases, but you can use the route command to add or modify routes should you need them. 
You can add squid as a (caching) web proxy, and something like dansguardian will allow you to do web content filtering.
You can probably do printer sharing with cups and/or samba, but I'm not familiar with that. 

Any linux distro can do this, but you probably want to start with a very minimal install and add the features/software you need, rather than starting from e.g. an ubuntu desktop. There are some specialised distros out there for this sort of thing, but I haven't used them so I won't comment.

I do routing and firewall on a 133 Mhz CPU with 64 MB RAM PC and that's more than enough. If you want to de squid e.a. on the same machine, you might need slightly more RAM and a disk that's large enough for your cache, but basically you could try with any old PC you find.

Here are some notes to get you started
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux1.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux1.htm)

---

### Post by madverb on 2009-02-08
You could try eBox. I have found it works pretty well and haven't had too much trouble implementing a firewall, proxy and web filter.

[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

---

### Post by hictio on 2009-02-08
Another option might be [IPCop](http://www.ipcop.org/), it's free, incredibly easy to setup, and (depending on our newtwork size) you can install it on pretty, pretty old hardware.

---

### Post by Chayak on 2009-02-08
I'd recommended Vyatta.  I haven't used the proxy functions on it yet but I've installed a number of their routers to replace Cisco equipment and I've not been disappointed yet.

---

### Post by cariboo on 2009-02-08
I agree with the poster who suggested ipcop, it is easy to setup, and you administer it with a web interface.

Jim

---

### Post by RFXCasey on 2009-04-13
Thanks for all the info guys. I know I am a little late with this reply but just been caught up in life for a while. So, no one mentioned Smoothwall Express, why is that? I hear a lot of people saying IPcop is better. If so why? Will IPcop do print serving? It's not critical or anything but it would be a really nice feature to have while the machine is running.

---

### Post by cariboo on 2009-04-13
With a pc based firewall/router, it comes down to a matter of what works best for you. The last time I set one up I used [Aron's Iptables Firewall]("http://rocky.eld.leidenuniv.nl/"), it looks pretty complicated, but it is so well commented, that anyone can use it.

Arno's iptables firewall is in the repositories. The installation script does a good job of setting up the basics.

Jim

---

### Post by RFXCasey on 2009-04-14
I have 2 network cards in the machine I am trying to use as the firewall. The software I am using is Smoothwall Express. I was thinking I would run a network cable from the cable modem to the firewall machine and then another cable from the firewall to my main computer just to keep it simple while setting everything up. After I get it to work so I could access the firewall configuration screen with my web browser and getting internet access passed through the firewall to my main computer I was going to unhook my pc from the firewall machine and replace it with my Belkin router which I could then hook all my other computers up to. So in effect I was thinking I could just use the firewall machine as a firewall with stateful packet inspection and a webfilter and leave the actual routing part up to my Belkin router. Will that work like that? I have reset all my router settings so that it will basically pass or accept anything. I am trying to use Smoothwall Express right now and it installs just fine. It autodetects my network cards with no problem. So right now I have the network going from the cable modem to the firewall (Red?) side and then the (Green?) side to my main machine. I cannot however access the web server configuration screen from my browser. I have switched the cables around from red to green and still can't access it. Any ideas on what I should check? I was also wondering if I should be using a crossover cable from the firewall machine to my main computer? This is all pretty complicated when it doesn't work right.

---

### Post by cmuxed on 2011-01-22
It sounds like there are two things you need to check here before proceeding;

- yes i would be using a crossover cable to connect from one pc to another directly.  These days some network cards can handle just using standard cables but it sounds like you are using some pretty old tech, so use the crossover cable
- remember, if the router is now out of the picture, you will need to set static ip addresses for the two nics connected by the crossover cable.

---


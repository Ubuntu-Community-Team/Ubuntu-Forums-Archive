---
title: "Does A Router Provide Better Security?"
date: 2010-06-09
forum: Security
---

### Post by TheNewbieGeek on 2010-06-09
Hi I am thinking of getting a router for my linux tower because I thought it might provde another layer of protection. Does it provide better security? Do you have to install a server and would this make my tower vulnerable? Do you need to buy a router that is compatible with ubuntu or can you buy anyone you like? Thanks for the replies.

---

### Post by BoneKracker on 2010-06-09
> **TheNewbieGeek said:**
> Hi I am thinking of getting a router for my linux tower because I thought it might provde another layer of protection. Does it provide better security?
Yes.  Most routers made for home use have built-in features that enhance the security of machines behind them.  These include Network Address Translation (NAT) and connection tracking.  If you set one of these up between the internet and your computer, and you don't open any ports on it, then the only computers out there on the internet that can talk to your computer(s) are the ones that your computer(s) have initiated a "conversation" with.  Other attempts by computers on the Internet to connect to your computer(s) will "bounce off".

Basically, this does the same job as a software "firewall" on your computer, but it protects all the computers on your network.  It may sound redundant, but an extra layer of protection is often a good thing.  People have a way of mis-configuring the firewalls on their computers.  Also if you have more than one computer, you want to let them talk to each other (e.g. file sharing) without having the rest of the Internet being able to share your files too.

So, a router is most valuable if you have more than one computer and a home network.  However, because they typically have built-in firewall capabilities, it can be a nice security barrier even if you only have one.  It also gives guests you might have over a place to plug in so they can use the Internet.

> **TheNewbieGeek said:**
> Do you have to install a server and would this make my tower vulnerable? Do you need to buy a router that is compatible with ubuntu or can you buy anyone you like?
No, you don't have to install a server.  Yes, you can buy any one you like.  You might want to ask for advice in here about which one to get though.

---

### Post by TheNewbieGeek on 2010-06-09
I have been told that a router provides better security even for just one tower. What router do you recommend? Thanks for the replies.

---

### Post by iponeverything on 2010-06-09
> **TheNewbieGeek said:**
> I have been told that a router provides better security even for just one tower. What router do you recommend? Thanks for the replies.

something that runs dd-wrt.

---

### Post by TheNewbieGeek on 2010-06-09
Why is that better?

---

### Post by Linuxforall on 2010-06-09
Netgear has solid build and runs cool, comes with hefty power supply, also Billion and Zyxel make good ones. D link with game fuel tech if you are into heavy P2P and online gaming.

---

### Post by WinstonChurchill on 2010-06-09
If you're just talking about one server, a router is a silly redundancy - there's nothing a router that costs less than $1000 will do that iptables won't. Check out this link: [URL="http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html"]http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html
[/URL]
Forgive me if I'm underestimating your understanding of networking, but I'm betting you already have a "router" - is this server at your house? If it's IP Address is 10.x.x.x, 192.168.x.x, or 172.[16-31].x.x, then you already have a "router", and adding another one would do absolutely nothing. If your server actually has a public IP address, then yes, adding a "router" would hide it behind a NAT - but then you have to hassle with port-forwarding and the like, plus you're limiting the number of connections you can have at any given time to whatever the "router" can handle. NAT is really just security by obscurity - any services you want globally accessible will be just as vulnerable as if you had no fire-walling at all. And anything you want fire-walled can easily be blocked with the aforementioned iptables.

See also:  
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)
[http://www.faqs.org/rfcs/rfc1631.html](http://www.faqs.org/rfcs/rfc1631.html)

**EDIT: I was assuming your intent was to run a server... I'm not sure how I got that out of what you wrote; if this is just a desktop computer, than ignore everything I just said.**

---

### Post by BoneKracker on 2010-06-09
> **Linuxforall said:**
> Netgear has solid build and runs cool, comes with hefty power supply, also Billion and Zyxel make good ones. D link with game fuel tech if you are into heavy P2P and online gaming.

I think a good buy right now is the Netgear WNR3500L:

Wired Gigabit
Wireless N
Fat specs

(Broadcom MIPS 74K CPU (480 MHz), 8 MB Flash, 64 MB RAM).  Ample resources to run any open firware (DD-WRT, OpenWRT, Tomato, etc.) Wiki to facilitate using open firmware [http://www.myopenrouter.com/](http://www.myopenrouter.com/)

As a new linux user, you probably don't want to jump into running open firmware on your router, which can be kind of technical.  But, it's a good idea to get a router that is _capable_ of doing so.  In general, they have more flash and more ram, and they aren't as likely to skimp on the hardware.

That said, they tend to cost a bit more, so if you're pinched, just get what you can afford.  If you go looking for this one, make sure it says "L" on the box (WNR3500L).  I don't know where you are, but I actually bought mine off the shelf in a Staples office-supply store.

Also, Winston is right that, if you only have one computer, this isn't necessary.  It does, however, add a layer of protection in addition to giving you a place to plug in other devices later.  In information security, "redundancy" is not a bad word.  Also, "security by obscurity" is under-rated; it's a catchy phrase used by people who typically don't understand security concepts such as "attack surface".  Furthermore, if you're confident enough in your router's firewall and don't feel the need for redundancy, then you don't need to run a firewall on your computers, which frees them from the processing load of running the firewall.  I, for example, don't run iptables on any of my machines except my router/firewall.

---

### Post by TheNewbieGeek on 2010-06-09
> **]WinstonChurchill said:**
> If you're just talking about one server, a router is a silly redundancy - there's nothing a router that costs less than $1000 will do that iptables won't. Check out this link: [URL="http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html"]http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html
[/URL]
Forgive me if I'm underestimating your understanding of networking, but I'm betting you already have a "router" - is this server at your house? If it's IP Address is 10.x.x.x, 192.168.x.x, or 172.[16-31].x.x, then you already have a "router", and adding another one would do absolutely nothing. If your server actually has a public IP address, then yes, adding a "router" would hide it behind a NAT - but then you have to hassle with port-forwarding and the like, plus you're limiting the number of connections you can have at any given time to whatever the "router" can handle. NAT is really just security by obscurity - any services you want globally accessible will be just as vulnerable as if you had no fire-walling at all. And anything you want fire-walled can easily be blocked with the aforementioned iptables.

See also:
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)
[http://www.faqs.org/rfcs/rfc1631.html](http://www.faqs.org/rfcs/rfc1631.html)

Yes it is for my sole tower at home. I know ubuntu has iptables or a firewall but I was told that a router provides another layer of protection not better protection. I don't run a server and was told I didn't have to. If this is incorrect information please let me know.

---

### Post by WinstonChurchill on 2010-06-09
> **TheNewbieGeek said:**
> Yes it is for my sole tower at home. I know ubuntu has iptables or a firewall but I was told that a router provides another layer of protection not better protection. I don't run a server and was told I didn't have to. If this is incorrect information please let me know.

Yes, you're fine - I've been in "server mode" all day and I was watching Glee while I was writing that post... sorry if I confused you.

---

### Post by rookcifer on 2010-06-09
If you don't need Wireless-N support, then I suggest the Linksys WRT54GL.  They're cheap, open-source friendly, and can be flashed with Tomato.

---

### Post by HermanAB on 2010-06-09
Most routers actually run Linux.

---

### Post by anomie on 2010-06-09
[QUOTE=TheNewbieGeek]Do you need to buy a router that is compatible with ubuntu or can you buy anyone you like?[/QUOTE]

In terms of the OSI model, the so-called "home router" will be handling layer 2 (switching), layer 3 (routing), and layer 4 (PAT and/or port forwarding). The OS should be totally irrelevant. 

In practice, though, it would be prudent to read the fine print before you buy. Some offerings include Windows client software for quick configuration. (*Most* also offer web configuration too, though.) 

FWIW, I have owned a couple low-cost home routers from both Linksys and Netgear. They both provided a web interface for administration, and they played nice with Linux client hosts (they didn't require Internet Explorer or anything ridiculous).

---

### Post by SteamInc on 2010-06-09
If you really want a good one you could get a Cisco router. They are sort of expensive, but they have extremely good security.

---

### Post by bodhi.zazen on 2010-06-09
> **TheNewbieGeek said:**
> Yes it is for my sole tower at home. I know ubuntu has iptables or a firewall but I was told that a router provides another layer of protection not better protection. I don't run a server and was told I didn't have to. If this is incorrect information please let me know.

We are using the term "router" here somewhat loosely. A router performs several functions:

1. In the context of security, you are talking using the firewall function in the router. This can be emulated by iptables, however a router will be more secure as it has less applications running. Less applications = more secure.

If you use Linux or BSD as a router, be sure to run a minimal install or a distro that is router specific. There are several options, ipcop, etc ...

2. DHCP. On a SBHO or LAN people use the router to assign client IP addresses.

3. As a switch. Routers allow you to share an internet connection across multiple computers and allow you to file share (sambs, nfs, etc) behind the router's firewall.

4. Wireless. Most modern routers include wireless (WAP).

5. Some routers allow content filtering or other functions. For example you can black list porn sites or only allow internet access at certain times of the day. These features vary widely across routers.

6. Some routers have VPN ports built in.

So a better question is what do you wish to use a router for ? If only for "security" you could use ufw or iptables, but you will be more secure with a router only because a router has less software then your desktop. If nothing else, fewer installed applications == less vulnerabilities.

---

### Post by bodhi.zazen on 2010-06-09
I merged your two threads as they seem to be asking the same question.

---

### Post by BoneKracker on 2010-06-09
> **bodhi.zazen said:**
> I merged your two threads as they seem to be asking the same question.

I told him to create a separate thread to ask what router to get. :lol:

Unfortunately, in that second thread, everybody immediately started questioning whether he needed one or not, answering questions he never asked, and giving him advice that was redundant with the first thread.

He already knows that a router/firewall is redundant with an on-system firewall if he only has one computer.  He understands that it isn't the router that offers enhanced security, but the features that are provided by most home routers (firewall, NAT, etc.).  He understands the plusses and minuses of getting one.

He wants to get one (or at least seriously consider it).

The advice he needs now is which one to get.

---

### Post by bodhi.zazen on 2010-06-09
> **BoneKracker said:**
> I told him to create a separate thread to ask what router to get. :lol:

LOL

> The advice he needs now is which one to get.

Well, that question is almost always a matter of opinion and IMO is a better topic for the cafe the the security section.

---

### Post by BoneKracker on 2010-06-09
> **bodhi.zazen said:**
> LOL



Well, that question is almost always a matter of opinion and IMO is a better topic for the cafe the the security section.
I failed to specify the forum when I suggested a separate thread.

---

### Post by Morbius1 on 2010-06-09
> **rookcifer said:**
> If you don't need Wireless-N support, then I suggest the Linksys WRT54GL.  They're cheap, open-source friendly, and can be flashed with Tomato.
This router actually brings up an interesting problem with some routers. If I remember correctly it can't do "static DHCP" ( or "reserved DHCP", "reserved leases", "Pre-assigned DHCP", or whatever it's called :p )

What this feature allows the router to do is assign the exact same ip address to the exact same machine based on the machines NIC MAC address. It's easier to assign static ip address from the router than from within the OS itself and really comes in handy when dealing with Samba, CUPS, and other sharing systems.

I believe flashing with DD-WRT brings that capability to this particular router and I'm guessing that Tomato does as well.

---


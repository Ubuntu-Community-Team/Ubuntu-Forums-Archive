---
title: "Ubuntu as Gateway/Router"
date: 2013-12-10
forum: Server Platforms
---

### Post by wlraider70 on 2013-12-10
I'm considering setting up a Linux gateway. My small business network is getting a larger and the home router is a bit light on features. 

Here are a few things I'm looking to accomplish:

-Setup Dan's guardian or other other content filter
-Monitor bandwidth 
-QoS
-VPN

- all the other regular stuff 
- I'd like an ubuntu based solution as I'm most familiar with it. 


I've seen [http://www.zentyal.org/](http://www.zentyal.org/) and it looks cool, anyone have a review or competitor.

---

### Post by CharlesA on 2013-12-10
I've tried it before and while it works fine, I think the majority of the routing and NAT was done in iptables.

If you really want a firewall/routing appliance on a *nix box, check out pfSense, M0n0wall or Smoothwall.

---

### Post by nerdtron on 2013-12-11
Not very well Ubuntu but still close to UNIX concepts are mikrotik routers. VPN, routing, firewall, wifi hotspot etc. in a small package. They are also cheap. Just my two cents. :)

---

### Post by sandyd on 2013-12-11
If your looking to add more features to the network as well, I suggest Zentyal as well. It already has all prebuilt setups for a Small Business Server (LDAP Server, FTP, quotas, .etc .etc).
It has an easy to configure webgui. I use it at home to configure most networking services

Another option is ClearOS, which is essentially the same thing, except that it is based on CentOS (I think?)

---

### Post by houstonbofh on 2013-12-11
I would second pfSense if you want filtering and m0n0wall if you want a good routing firewall.  Both are FreeBSD based, and very easy to work with.  Also, Untangle has a community version, and it is actually Linux.

---

### Post by NotWindows on 2013-12-11
I have a simular question though I am totally new to firewalls, networking and servers. I want to run my business computer with Windows since my business software requires it unfortunately, but I need the security of Ubuntu or linux frontend. What is the best way for me to accomplish this?

I wish I could use Ubuntu on the business computer but need for my business software to be dependable and not have to realy on Wine etc. Right now Quickbooks doesn't want to work and leaves me to use Windows.

Thanks,
Kevin

---

### Post by CharlesA on 2013-12-11
Windows can be as security as Linux or OSX if you set it up that way. If you still want to run Linux as the Host OS and run Windows in a VM, that would probably work for you.

---

### Post by NotWindows on 2013-12-11
I am not very knowledable in setting Windows up to be secure other than thinking it always seems all of the security costs money. I have been using Ubuntu for 4 years with no issues and I use windows for a very short time and have viruses. It seems after installing everything to protect the computer it makes it even slower. I am just spoiled with how secure Ubuntu has been for me.

---

### Post by wlraider70 on 2013-12-11
What I'm trying to do is replace my standard home router with a full linux machine, so that its more like a standalone hardware firewall. I don't believe such a thing is necessary for security . As long as you are running SOME firewall. Your windows machines also have a firewall on them. 

More than anything I would say be careful what programs you install.

---

### Post by CharlesA on 2013-12-11
> **wlraider70 said:**
> What I'm trying to do is replace my standard home router with a full linux machine, so that its more like a standalone hardware firewall. I don't believe such a thing is necessary for security . As long as you are running SOME firewall. Your windows machines also have a firewall on them. 

You can do that with Ubuntu or pick one of the suggestions mentioned above. Depending on what you actually want the machine to do, you could probably run it off something like a Raspberry Pi (assuming you use a USB network card for the LAN or WAN port).

---

### Post by newbie-user on 2013-12-12
I prefer pfsense. It's free and very easy to set up. It's comes with VPN and RRD graphs ootb and you can quickly install extra packages such as Dansguardian from the web interface.

---

### Post by SeijiSensei on 2013-12-15
> **CharlesA said:**
> you could probably run it off something like a Raspberry Pi (assuming you use a USB network card for the LAN or WAN port).

The Pi comes with one Ethernet jack. For the second interface, you can add a wifi connection easily with a USB device like [this](http://www.amazon.com/gp/product/B003MTTJOY/).  For a second Ethernet connection, you'll need a USB to Ethernet adapter as Charles suggests.

I wonder, though, if your needs could not be met with a good commercial router that runs dd-wrt or Tomato, two Linux derivatives designed for routers.  [Buffalo]("http://www.buffalotech.com/products/wireless/single-band-wireless-routers") makes routers that come with dd-wrt as the stock firmware.

---

### Post by CharlesA on 2013-12-15
> **SeijiSensei said:**
> 
I wonder, though, if your needs could not be met with a good commercial router that runs dd-wrt or Tomato, two Linux derivatives designed for routers.  [Buffalo]("http://www.buffalotech.com/products/wireless/single-band-wireless-routers") makes routers that come with dd-wrt as the stock firmware.
That would be one of my thoughts, too.

I've got DD-WRT running off a DIR-615, but it's limited to the micro build as the memory and flash space available is quite low. I've heard those buffalo routers are pretty nice with DD-WRT, but I've seen no reason to replace the one I have now.

---


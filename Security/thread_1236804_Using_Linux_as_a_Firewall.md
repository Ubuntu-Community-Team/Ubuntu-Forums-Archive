---
title: "Using Linux as a Firewall"
date: 2009-08-10
forum: Security
---

### Post by chessnerd on 2009-08-10
Alright, I may soon acquire an old computer from my aunt. I could run Ubuntu or some other distro on it, but I think I'd like to set it up to act as a firewall for the other computers in my house. So, I have 4 questions:

1. What Linux distro should I use to do this?
2. What hardware will I need?
3. What software will I need?
4. What potential problems might this cause?

I have a general understanding of how to configure firewalls on desktop computers, but I don't know much about how to make a computer act like one. So, if someone could point me to a good online guide that explains how to configure this once I have everything ready to go that would be great.

---

### Post by jeffathehutt on 2009-08-10
> **chessnerd said:**
> 
1. What Linux distro should I use to do this?
2. What hardware will I need?
3. What software will I need?
4. What potential problems might this cause?


1. Ubuntu can work fine as a firewall / network server.  Since you are posting on the ubuntu forums, I assume you are somewhat familiar with it.  There are many others though; ipcop is supposed to be very good.  Really, whatever distribution you are familiar with will most likely work.

2. Most computers can be used as a small firewall.  You will need two network cards installed, as well as a network switch large enough to plug the rest of your computers into.

3. [eBox]("http://ebox-platform.com") is a modified Ubuntu system designed for easy administration.  You can access eBox through a web browser and control most of the important parts of the server from there.

4. I'm not sure of any specific problems you might run into, but you could always get help from the forums if you get stuck or if something doesn't work.

Hope that helps a bit :)

---

### Post by chessnerd on 2009-08-10
> **jeffathehutt said:**
> 2. Most computers can be used as a small firewall.  You will need two network cards installed, as well as a network switch large enough to plug the rest of your computers into.
Cool, then I should be set for hardware. So, do I just run an ethernet cable from the modem to the computer and then from the computer to the router or is there something else I need to do hardware wise?

> **jeffathehutt said:**
> 3. [eBox]("http://ebox-platform.com") is a modified Ubuntu system designed for easy administration.  You can access eBox through a web browser and control most of the important parts of the server from there.
Okay. Apparently eBox can be installed from scratch onto the computer like any other distro. After it is installed can I then just disconnect the monitor and keyboard and access the configuration options via a browser on another computer? Or should I configure it first and then disconnect everything?

---

### Post by jeffathehutt on 2009-08-11
> Cool, then I should be set for hardware. So, do I just run an ethernet cable from the modem to the computer and then from the computer to the router or is there something else I need to do hardware wise?

Well, there are multiple ways to do it.  If you use ipcop or ebox (or many others), then your computer will actually *become* the router.  In that case, the setup would be:
Modem -> firewall/router (your new computer) -> switch -> other computers

You would run a cable from the modem to one network card (WAN), then a cable from the other network card to the switch (LAN), then all other computers connect to the switch.  This way, all computers on your network are required to go through the firewall / router, and thus be protected.

> Okay. Apparently eBox can be installed from scratch onto the computer like any other distro. After it is installed can I then just disconnect the monitor and keyboard and access the configuration options via a browser on another computer? Or should I configure it first and then disconnect everything?

I have never personally set up ebox, so I'm not sure how to set it up exactly.  You would need the connection to the modem set up, but that could probably be done automatically by dhcp once you boot the computer.  Then, you would need to set up the IP address on the LAN, that might also require a monitor and keyboard attached, but I assume this is done as you install the operating system.  Once you have the LAN IP, you would no longer need the monitor and keyboard, since you would just access the box with a web browser on another computer.

---

### Post by bodhi.zazen on 2009-08-12
In general I would not use Ubuntu as a router. You should use a router specific distro, such as ipcop and / or smoothwall .

[http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

If you can tolerate it engarde linux would be nice as well (it uses shorewall and selinux, it very very secure, whichis what you want in a router).

In general router specific distros, as opposed to Ubuntu. install minimal applications. Less applications = less potential security breaches.

---

### Post by Whiffle on 2009-08-12
You might look into getting a dedicated hardware router instead.  Chances are that old computer pulls 50 watts or more, while a small dedicated router probably pulls no more than 10 watts.  If you're running this 24/7/365, the difference adds up.  But, if you're using it for more than a firewall, which may or may not be a good idea (i'm not a security expert), then its less of a waste of power.

---

### Post by TuckLive on 2009-08-12
> **bodhi.zazen said:**
> In general I would not use Ubuntu as a router. You should use a router specific distro, such as ipcop and / or smoothwall.

I just installed Smoothwall on an extra box I had.  Easy install and web gui for making rules and modifications

---

### Post by Jekshadow on 2009-08-12
1) Personally, I think that Linux is great for general use and Servers, but when it comes to Firewalls, I recommend BSD. It is not Linux based (similar and open source though) but I personally think it is more secure. Look at [http://www.pfsense.com/](http://www.pfsense.com/)

2) For pfSence, 100mhz processor and 128MB RAM. In other words, if BSD supported the ARM architecture, an iPhone 2G or an iPod Touch 1G (the first versions) could run it.

3) It is a firewall BSD distribution, and comes with anything you might need.

4) It may block certain services that you use. If you do not connect to your computer from outside of your network (aka, using SSH or Remote Desktop to connect to your home computer from work) you should be fine.

---

### Post by HermanAB on 2009-08-14
Howdy,

Most commercial routers run Linux, so you are on the right track.  Also, it doesn't matter what version of Linux you use, since at that low level, they are all the same.  

So all you need to do is read Rusty Russel's Amazingly Inaccurate Web Sites for the latest information on netfilter and iptables.

[http://kerneltrap.org/node/892](http://kerneltrap.org/node/892)
[http://www.ozlabs.org/~rusty/](http://www.ozlabs.org/~rusty/)
[http://netfilter.org/](http://netfilter.org/)

---


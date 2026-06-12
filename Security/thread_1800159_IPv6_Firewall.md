---
title: "IPv6 Firewall"
date: 2011-07-08
forum: Security
---

### Post by atlgg on 2011-07-08
I am about to be part of an IPv6 broadband trial and I am planning to set up my own IPv4/6 firewall since the NAT based firewall in my current router will not be up to the task and I do have devices on my home network which cannot be secured.

Here are my requirements:
- both interfaces will use internal IP addresses
- dual stack interfaces
- stateful firewall
- headless GUI management
- per application pin-holing would be nice but not required
- VPN pass through (work) is required

Here is my network topology:
Internet
     |
     |
Modem (DSL)
     |
     |
Firewall
     |
     |
Router/Switch

I am still getting details on the modem to be used but I expect that the modem will be the address assigning agent and act as the default gateway (dual stack).  My current router will be changed to a switch and wireless access point.

I am planning to use a Biostar H6 barebones box with a G620 processor and 2-4GB of ram and some sort of SATA HD.

Ideally I would like this to be a transparent bridge firewall with full stateful capability.  I do have experience with Linux admin and firewall admin (checkpoint mainly).

I am not looking for a tutorial but more trying to figure out the right mix of packages to use to build this.  Any help is greatly appreciated.

---

### Post by Dangertux on 2011-07-08
> **atlgg said:**
> I am about to be part of an IPv6 broadband trial and I am planning to set up my own IPv4/6 firewall since the NAT based firewall in my current router will not be up to the task and I do have devices on my home network which cannot be secured.

Here are my requirements:
- both interfaces will use internal IP addresses
- dual stack interfaces
- stateful firewall
- headless GUI management
- per application pin-holing would be nice but not required
- VPN pass through (work) is required

Here is my network topology:
Internet
     |
     |
Modem (DSL)
     |
     |
Firewall
     |
     |
Router/Switch

I am still getting details on the modem to be used but I expect that the modem will be the address assigning agent and act as the default gateway (dual stack).  My current router will be changed to a switch and wireless access point.

I am planning to use a Biostar H6 barebones box with a G620 processor and 2-4GB of ram and some sort of SATA HD.

Ideally I would like this to be a transparent bridge firewall with full stateful capability.  I do have experience with Linux admin and firewall admin (checkpoint mainly).

I am not looking for a tutorial but more trying to figure out the right mix of packages to use to build this.  Any help is greatly appreciated.

Well minus the Headless GUI I would say it sounds like you need to build an iptables script for the machine. So if GUI is a huge deal to you then, iptables may not work out for you.

I am assuming your router/switch will be doing the NAT'ing to the rest of the network? Because many current solutions don't support both NAT for 4 and 6. 

You might also want to look into the mf-firewall suite, although I'm not sure if they even have a GUI. The GUI is really gonna kill you on this task I think. You may just have to eat it on the CLI part, or write your own front end :-/

Shorewall6 is a decent third alternative, it provides the GUI you are looking for but is much less configurable then either of the other two options.  Shorewall6 also provides no NAT, so if that is needed you won't be able to utilize it for this project.

Edit : On a sidenote, I wish I had your ISP :-(

---

### Post by atlgg on 2011-07-08
Thanks for the reply.  On the GUI side I can use webmin of I need to.  I can do the CLI but I am also looking for something I could recommend to friends.  Your reply goes along with what I was thinking but I wanted to double check.

The way the plans currently are I think the modem will do the v4 NAT.  As for the ISP I got lucky enough to be part of the internal "friendly" trial.  I have been working on IPv6 stuff for a while.  I cannot really post more now but after I get this set up I will post on what I used and how it has worked out.

---

### Post by SoftwareExplorer on 2011-07-08
If you are going to use Ubuntu on the firewall, I would recommend using UFW. You can enable it for IPv6 by changing "IPv6=no" to "IPv6=yes" in /etc/default/ufw. I haven't actually used it to firewall forwarding on my network because I prefer host based firewalls. Even if it doesn't directly support it through UFW, UFW has files you can drop rules into and it will automatically add the rules at startup without you having to hack together some startup script. I have used UFW on my main router desktop (yes, my desktop is my network's router) with a hairpin NAT setup. While UFW didn't directly support the NAT setup, I could put the rules in /etc/ufw/before.rules to have the rules automatically loaded.

By the way, if your modem is IPv6 enabled, it may already have a stateful firewall built in. 

I wish I had your ISP. (Mine said they would have it sometime this year. I asked them in January. I'm trying to be patient and not ask them "Is it ready yet?")

---

### Post by bodhi.zazen on 2011-07-08
> **SoftwareExplorer said:**
> If you are going to use Ubuntu on the firewall, I would recommend using UFW. You can enable it for IPv6 by changing "IPv6=no" to "IPv6=yes" in /etc/default/ufw. I haven't actually used it to firewall forwarding on my network because I prefer host based firewalls. Even if it doesn't directly support it through UFW, UFW has files you can drop rules into and it will automatically add the rules at startup without you having to hack together some startup script. I have used UFW on my main router desktop (yes, my desktop is my network's router) with a hairpin NAT setup. While UFW didn't directly support the NAT setup, I could put the rules in /etc/ufw/before.rules to have the rules automatically loaded.

By the way, if your modem is IPv6 enabled, it may already have a stateful firewall built in. 

I wish I had your ISP. (Mine said they would have it sometime this year. I asked them in January. I'm trying to be patient and not ask them "Is it ready yet?")

I do not think gufw has options for nat / port forwarding, etc.

Personally I would use any of the linux distros specifically geared to run as a firewall over Ubuntu ;)

---

### Post by Dangertux on 2011-07-08
> **bodhi.zazen said:**
> I do not think gufw has options for nat / port forwarding, etc.

Personally I would use any of the linux distros specifically geared to run as a firewall over Ubuntu ;)

gufw does not however I am fairly certain that ufw scripts can be configured to. As they share most of the basic functions of iptables that they control. Some of the more advanced iptables functionality is not suPported (eg: tarpit). However I believe NAT and forwarding are. 

I could be wrong though I am not at a system I can verify that on ATM.

---

### Post by bodhi.zazen on 2011-07-08
> **Dangertux said:**
> gufw does not however I am fairly certain that ufw scripts can be configured to. As they share most of the basic functions of iptables that they control. Some of the more advanced iptables functionality is not suPported (eg: tarpit). However I believe NAT and forwarding are. 

I could be wrong though I am not at a system I can verify that on ATM.

You can configure the scripts, but if you are going to do that it is honestly easier to just use iptables as you will need to know the iptables syntax in order to edit the ufw config files ;)

There are various blogs on how to do this :

[https://nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall](https://nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall)

But, those rules are extreemly basic and forward all traffic. You have not firewalled anything or allowed ports yet. So again, back to iptables and NAT to get the syntax, then once you have the syntax abbreviate it for ufw ...

so you see, ufw becomes more work then using iptables directly ;)

Again, if you want a graphical front end, look at something more like shorewall.

---

### Post by Dangertux on 2011-07-09
> **bodhi.zazen said:**
> You can configure the scripts, but if you are going to do that it is honestly easier to just use iptables as you will need to know the iptables syntax in order to edit the ufw config files ;)

There are various blogs on how to do this :

[https://nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall](https://nowhere.dk/articles/tip_nat_with_ubuntus_ufw_firewall)

But, those rules are extreemly basic and forward all traffic. You have not firewalled anything or allowed ports yet. So again, back to iptables and NAT to get the syntax, then once you have the syntax abbreviate it for ufw ...

so you see, ufw becomes more work then using iptables directly ;)

Again, if you want a graphical front end, look at something more like shorewall.


Yeah -- I looked into it, forgot about this thread though. To be honest for the application the individual is looking for UFW would be a massive time waster. 

I would stand by my original recommendation of iptables or shorewall6

---

### Post by atlgg on 2011-07-09
I am leaning towards iptables unless I find a better option in the next couple of weeks.  I mainly want the gui admin for a better visual representation of the rules I have created so webmin will be fine for that.  The info I have on the modems is that they will have capability to block incoming connections but no real stateful FW capability.  I do have two main purposes for doing this project:
1. Protect devices on the internal network not capable of protecting themselves especially if I can get them running IPv6.  Mainly gaming and video consoles.
2. I want to see what the extent of probing or attacks there are on IPv6 currently since the deployment of IPv6 will have a lot more machines with publicly routeable IP addresses and thus exposed.  I know I can find log file parsers to help with this.

I do plan on seeing how the various IPv6 capable devices on my home network do behave with IPv6 compared to IPv4 and of course if the dual stack mechanisms in a few different operating systems work as expected in real world use.

I may play around with a few different network topologies once I get everything up and working to see what works best.

Thanks for all the help and advice.

---

### Post by Dangertux on 2011-07-09
> **atlgg said:**
> I am leaning towards iptables unless I find a better option in the next couple of weeks.  I mainly want the gui admin for a better visual representation of the rules I have created so webmin will be fine for that.  The info I have on the modems is that they will have capability to block incoming connections but no real stateful FW capability.  I do have two main purposes for doing this project:
1. Protect devices on the internal network not capable of protecting themselves especially if I can get them running IPv6.  Mainly gaming and video consoles.
2. I want to see what the extent of probing or attacks there are on IPv6 currently since the deployment of IPv6 will have a lot more machines with publicly routeable IP addresses and thus exposed.  I know I can find log file parsers to help with this.

I do plan on seeing how the various IPv6 capable devices on my home network do behave with IPv6 compared to IPv4 and of course if the dual stack mechanisms in a few different operating systems work as expected in real world use.

I may play around with a few different network topologies once I get everything up and working to see what works best.

Thanks for all the help and advice.

Good luck :-)

You should keep us posted, I for one would be interested in your findings.

---

### Post by bodhi.zazen on 2011-07-09
> **atlgg said:**
> I am leaning towards iptables unless I find a better option in the next couple of weeks.  I mainly want the gui admin for a better visual representation of the rules I have created so webmin will be fine for that.  The info I have on the modems is that they will have capability to block incoming connections but no real stateful FW capability.  I do have two main purposes for doing this project:
1. Protect devices on the internal network not capable of protecting themselves especially if I can get them running IPv6.  Mainly gaming and video consoles.
2. I want to see what the extent of probing or attacks there are on IPv6 currently since the deployment of IPv6 will have a lot more machines with publicly routeable IP addresses and thus exposed.  I know I can find log file parsers to help with this.

I do plan on seeing how the various IPv6 capable devices on my home network do behave with IPv6 compared to IPv4 and of course if the dual stack mechanisms in a few different operating systems work as expected in real world use.

I may play around with a few different network topologies once I get everything up and working to see what works best.

Thanks for all the help and advice.

IMO iptables is best, of course you will also want ip6tables =)

---

### Post by wacky_sung on 2011-07-09
> **bodhi.zazen said:**
> IMO iptables is best, of course you will also want ip6tables =)

Fully agree.:guitar:

---


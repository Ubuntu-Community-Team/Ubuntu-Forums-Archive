---
title: "after reinstall boot very slow and no wireless at the hotel"
date: 2007-06-06
forum: System76 Support
---

### Post by perce on 2007-06-06
Last week I had to reinstall the Darter. Now the boot has become much slower (at least when I'm not plugged to an ethernet cable) because it stops about 30 seconds at "configuring interfaces". Moreover I can't connect to h wireless network in my hotel (note that it is a problem I had only on this hotel, Holyday Inn Princeton, not with other network.) This is the reason why I think the two problems are linked: in my file /etc/network/interfaces I have an entry 

auto eth1 
iface eth1 inet dhcp

which corresponds to he wireless card, I think. If I comment auto eth1 and reboot, the boot becomes fast again, but networkmanager doesn't detect wireless networks automatically anymore. No problem, I configure the wireless manually using iwconfig and dhclient, and now 
I can connect in my hotel. This is strange indeed, and somehow annoying.

---

### Post by tedrampart on 2007-06-07
I had the same problem with the slow boot up..

the link has the answer: [http://ubuntuforums.org/showpost.php?p=2776184&postcount=2](http://ubuntuforums.org/showpost.php?p=2776184&postcount=2)

---

### Post by thomasaaron on 2007-06-07
The problem with your wireless (and I think maybe the slow boot too) is your /etc/network/interfaces file.

Your file should look like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


Then, you can use the network manager icon (in the upper right corner of your monitor) for connecting to the Internet.

If you use System > Administration > Network, it hoses the interfaces file.

You should have to do PRECIOUS LITTLE (if any at all) configuration with Network Manager unless you're dealing with static IP's.

---

### Post by perce on 2007-06-07
Thank you Tom. Commenting out eth1 made the boot a lot faster. 

To connect at the hotel I have to disable wireless networking on Network Manager, and connect by hands using iwconfig and dhcp. Do you have an idea why? I think there is little I can do, but I would like to understand.

EDIT: I've noticed that the wireless in the hotel works if I connect via Network Manager, and then I request an IP address with dhclinet. It's like whatever Network Manager uses to conect to a dhcp server is not compatible with the network I'm using.

---

### Post by thomasaaron on 2007-06-08
I've noticed on my own Darter that, if given the choice between a wired and wireless network, it will go with the wired. And if I try to connect to wireless while a wired connection is available, it kind of trips over itself. That is, it will show that both a wired and wireless connection are selected. I wasn't sure if this is what you are experiencing.

It sounds like the hotel wireless might be set up as a static IP address. Otherwise, I wouldn't think it would require any manual configuration.

---

### Post by perce on 2007-06-08
> **thomasaaron said:**
> I've noticed on my own Darter that, if given the choice between a wired and wireless network, it will go with the wired. And if I try to connect to wireless while a wired connection is available, it kind of trips over itself. That is, it will show that both a wired and wireless connection are selected. I wasn't sure if this is what you are experiencing.


No, this is not the case. I never use wireless if I have a wired connection available. I haven't been connected to a wire for almost one week now.

> 
It sounds like the hotel wireless might be set up as a static IP address. Otherwise, I wouldn't think it would require any manual configuration.

Not really, because I get an address from the dhcp server if I use dhclient. It's only Network Manager that gets confuse by he server (or the server gets confused by Network Manager.

---

### Post by riseringseeker on 2007-06-09
> **perce said:**
> Thank you Tom. Commenting out eth1 made the boot a lot faster. 

To connect at the hotel I have to disable wireless networking on Network Manager, and connect by hands using iwconfig and dhcp. Do you have an idea why? I think there is little I can do, but I would like to understand.

I can relate to this, as someone who spends a lot of time in various hotels.

I have been able to connect to any hotel so far, though some of them were a little stubborn about it...

Thus far I have run into 3 different ways the wireless is offered.  

One is "just there" and requires nothing but having the wireless on and ready (roaming mode enabled).  

The second is when it opens a browser window relating to the hotel and you click on an icon that says you agree to their service policy.  

The third is when the front desk (or IT) gives you a username and password to use when logging in, and is largely a variation of #2 with a username and password required.

I have to assume you are dealing with #2 or #3 scenario at the hotel you are having problems with.  

Either way, what has worked for me (and very well may for you) is to go ahead and open a browser.  For some reason, it will not connect to the DHCP server and get the needed assignment when it opens your "home page".  Try clicking anything else that you have bookmarked, or type another URL into the address window (i.e. if your browser normally opens in [www.google.com](www.google.com), try typing in [www.yahoo.com](www.yahoo.com) - you get the idea).

> EDIT: I've noticed that the wireless in the hotel works if I connect via Network Manager, and then I request an IP address with dhclinet. It's like whatever Network Manager uses to conect to a dhcp server is not compatible with the network I'm using.


I have no idea why many hotels will not recognize the request when it comes from your home page, but will if you choose something else, but it has worked in every hotel I have tried it in all around the world for me - give it a shot, it's a cheap "fix".

I am pretty sure this is not a Ubuntu bug, if I had to guess it is something to do with Firefox under Linux (or maybe just Firefox - never tried it with windows).  I had the same thing happen to me when I ran Mandriva.  Before I stumbled across the method above, I would "hover" my cursor over the connection icon (I was using KDE) and then type the IP address it reported into the browser window to connect.

---


---
title: "Converting an old router into a switch"
date: 2010-06-09
forum: The Cafe
---

### Post by Yes on 2010-06-09
I only have one Ethernet jack in my basement, so I'd like to convert a spare router I have into a switch.  That way, I can have LAN parties down there.

I've found plenty of websites explaining what I need to do, but I need help with the first step - accessing the router's config page.  It's a Linksys BEFSR41, and the standard config page for it would be 192.168.1.1.  But of course when I go there, I get the config page for my Verizon router.  How would I get to the config page while it's not being used as the router?

Thanks!

---

### Post by Phrea on 2010-06-09
Add it as a service to your router using the mac address.

---

### Post by saulgoode on 2010-06-09
Connect a computer directly to the Linksys router to change the configuration.

---

### Post by juancarlospaco on 2010-06-09
*Switch is layer 2, router is layer 3.*

---

### Post by LowSky on 2010-06-09
If I'm not mistaken the address should be 192.168.0.1 and disconnect the Verizon modem if its still giving you issues. Then you should be able to log into the router, and change the things address to a number a bit higher to something like 192.168.0.200
All you have to do is not use the router port. Just connect your one Ethernet line in your basement to one of the 4 Ethernet ports on the router.

---

### Post by samalex on 2010-06-09
Getting to the admin page by default is only accessible when you're directly connected to the router whether wirelessly or wired.

I'd recommend connecting your computer directly to the router and if DHCP is enabled you should get an IP then hit [http://192.168.1.1](http://192.168.1.1) with password of 'admin' and see if you get in.  If you don't get an IP and don't remember/know the IP schema to setup a static IP then you may need to hard reset the router back to default.

Try that and see if it works, and if not post any errors and also how you have things wired up.

Sam

---

### Post by Pablo Pablovski on 2010-06-09
You'll need to change the IP of your "new" switch, to something other than 192.168.1.1. 

First, check the Verizon router's config to see what DHCP IPs it's set up to issue, and make a note of an unused IP outside that range (192.168.1.2, .100, .254, or whatever).

Then, disconnect / power off the Verizon router, so that there's only one device on your LAN with the 192.168.1.1 address. Then, logon to the switch and change its IP in the menus to the unused IP you picked out in the step above (remember that you'll lose connectivity to it when you change the IP - you might want to reboot it afterwards).

Check whether the switch is configured to issue DHCP addresses - if so, switch that function off (it'll only confuse matters if the Verizon router is also issuing IPs from the same subnet.

Re-connect the Verizon router, and logon to it and to the web to check all's well, and do the same to the new IP address of the switch.

I *think* that should work. If not, post back - if you can!

---

### Post by Yes on 2010-06-09
Woah, thank's for all the replies.

The first thing I did was hard reset the router.  I've tried directly plugging the router into my computer, via an Ethernet cable attached to one of the four normal ports on the back of the router (not uplink or WAN), but Firefox couldn't find anything at 192.168.1.1.  Any ideas?

I won't be able to unplug the Verizon router until much later tonight (i.e., when everyone's in bed), so I'll try all that stuff then.

---

### Post by lostinxlation on 2010-06-09
I don't get it.
The router works at the higher protocol layer than the switch and the router knows what the switch knows. A router runs ARP to obtain MAC address which is required for frame delivery on Data Link Layer, so...it knows how to deliver the packet to the specific physical address without being a switch.
I'm just curious why you want to turn the router to switch.

---

### Post by 98cwitr on 2010-06-09
> **juancarlospaco said:**
> *Switch is layer 2, router is layer 3.*

what about a layer 3 switch :?

essentially what you're doing is turning the router into a bridge.

Turn off DHCP, turn off DNS...for that matter turn off all protocols that you can other than it's obtaining an IP from the ISP (ISP will now literally be the verizon router). The router will still transfer data when connected to a router.

[http://homecommunity.cisco.com/t5/Wireless-Routers/Connecting-two-routers-wired-the-definitive-answer/m-p/47006](http://homecommunity.cisco.com/t5/Wireless-Routers/Connecting-two-routers-wired-the-definitive-answer/m-p/47006)

---

### Post by Yes on 2010-06-09
Yeah I know I'm not truly turning the router into a switch, I'm just disabling the features that would interfere with the other router, like DHCP.

Anyway, success!  I ran /etc/rc.d/network restart after connecting the router to my computer and then I was able to access it at 192.168.1.1.  I disabled DHCP, now lets see if it works...

---

### Post by lz1dsb on 2010-06-09
Frankly I didn't really get it. Linksys BEFSR41 has a built in switch. So this should work out of the box, even without configuring anything. According to the product description you even have an uplink port to connect to other such "switches". Why running DHCP is such a problem? A switch could be running a simple DHCP service and still operating on Layer 2. And if all hosts in your network are using static IP addresses, the DHCP won't matter anyway.

Cheers,
Boyan

---

### Post by 98cwitr on 2010-06-09
> **lz1dsb said:**
> Frankly I didn't really get it. Linksys BEFSR41 has a built in switch. So this should work out of the box, even without configuring anything. According to the product description you even have an uplink port to connect to other such "switches". Why running DHCP is such a problem? A switch could be running a simple DHCP service and still operating on Layer 2. And if all hosts in your network are using static IP addresses, the DHCP won't matter anyway.

Cheers,
Boyan

You dont want to have DHCP running on two connected devices...when the tables try to update they will conflict (for the clients, Im not talking about for the Ip assignment of the network device itself). Same goes for DNS.

It'll work...but it will get very very very slow very fast.

---

### Post by Yes on 2010-06-09
I don't understand much of the networking stuff, and it makes sense that a router would be able to act as a switch by default but it didn't when I tried it at first.  I disabled DHCP and set it to act as a gateway rather than a router and now everything is working!  Thank you so much, all of you :)

---

### Post by 98cwitr on 2010-06-09
> **Yes said:**
> I don't understand much of the networking stuff, and it makes sense that a router would be able to act as a switch by default but it didn't when I tried it at first.  I disabled DHCP and set it to act as a gateway rather than a router and now everything is working!  Thank you so much, all of you :)

you dont have the router plugged into the WAN port do you? If you do, unplug it and put it in another port.

---

### Post by Yes on 2010-06-09
> **98cwitr said:**
> you dont have the router plugged into the WAN port do you? If you do, unplug it and put it in another port.

Nope, it's in one of the normal 1-4 ports.

---

### Post by lz1dsb on 2010-06-10
> **98cwitr said:**
> You dont want to have DHCP running on two connected devices...when the tables try to update they will conflict (for the clients, Im not talking about for the Ip assignment of the network device itself). Same goes for DNS.

It'll work...but it will get very very very slow very fast.

I didn't really understand what do you mean. Are you saying that having a DHCP service will slow down the network? What I was saying is that if he has his ip configs statically configured on all hosts, whether you have DHCP enabled or not, it doesn't really matter. DHCP only responds to queries, so if you don't send any, there won't be a response from the DHCP server. Well anyway, we're for sure quite out of the topic... The important point here is, that the problem is solved!

Cheers,
Boyan

---

### Post by 98cwitr on 2010-06-10
> **lz1dsb said:**
> I didn't really understand what do you mean. Are you saying that having a DHCP service will slow down the network? What I was saying is that if he has his ip configs statically configured on all hosts, whether you have DHCP enabled or not, it doesn't really matter. DHCP only responds to queries, so if you don't send any, there won't be a response from the DHCP server. Well anyway, we're for sure quite out of the topic... The important point here is, that the problem is solved!

Cheers,
Boyan

yeah, and when two routers continuously query each other you're going to have a slow network...you dont want to have two DHCP servers conflicting with each other.


> **Yes said:**
> Nope, it's in one of the normal 1-4 ports.


good call, you're fine then.

---


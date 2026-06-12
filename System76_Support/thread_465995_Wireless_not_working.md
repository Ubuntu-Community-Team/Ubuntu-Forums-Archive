---
title: "Wireless not working"
date: 2007-06-06
forum: System76 Support
---

### Post by cward002 on 2007-06-06
Hi. I just tried last night to get my Gazelle performance hooked up to my wireless at home last night. Unfortumnately, it didn't work. I know the wireless works because I can connect to hot spots in other locations. I first tried in ad-hoc mode without a router and then in infrastructure mode with a router but no dice. Network Manager can see the Access Point but it cannot connect even to the configuration page.

I am not sure what else to try. I will post my resolv.conf when I get home.

If there is any other information you need, please let me know.

Thanks

Colin

---

### Post by thomasaaron on 2007-06-06
Have you tried to configure your router?
(You will probably have to connect to the router with a wired connection to do that.)

I would suggest:
* 64-Bit hex WEP key
* Set to Open System (as opposed to shared key / default settings)

Then, when you click on the access point via network manager (the icon in the upper right of your monitor) you should be prompted for a wep key.

---

### Post by cward002 on 2007-06-06
Hi Thomasaaron.

yes I tried with a wried router attached to the access point. but I still could not access the IP address of the Access Point. Network manager still says I have no connection. I know it is something simple I am overlooking.

---

### Post by thomasaaron on 2007-06-06
Are you saying you cannot get into your router with a WIRED connection too?
What brand router are you using?
(The IP address of linksys routers is 192.168.1.1)


Also, have you tried to establish a connection using System > Administration > Network?
If you have, your /etc/network/interfaces file is probably hosed.

If that's the case, let me know, and I'll tell you how to fix it.

---

### Post by cward002 on 2007-06-06
Thats correct. I cannot access my network even with a wired router. I have to plug the ethernet cable directly into the modem to get it to connect. It is a pppoe connection if that helps. I will post my /etc/network/interfaces file when I get home this afternoon. The Access Pont and the router are both D- Links.

thanks for your help

Colin

---

### Post by thomasaaron on 2007-06-06
With your computer connected via wire to the router, go to a terminal (Applications > Accessories > Terminal) and enter the following command:
[HTML]
ifconfig[/HTML]

(and post your /etc/network/interfaces file too...)

---

### Post by cward002 on 2007-06-06
I will send those files as soon as I get home

Again thx for all your help thomasaaron


Colin

---

### Post by cward002 on 2007-06-06
Here is the output of ifconfig:


eth1      Link encap:Ethernet  HWaddr 00:18:F3:EC:07:0A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19479 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12229855 (11.6 MiB)  TX bytes:2229018 (2.1 MiB)
          Interrupt:16 Base address:0x4c00 

eth2      Link encap:Ethernet  HWaddr 00:1B:77:10:CC:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:56026 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 Memory:fe1ff000-fe1fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:253799 (247.8 KiB)  TX bytes:253799 (247.8 KiB)

and here is the contents of my interfaces:

# The loopback interface
# Interfaces that comes with Debian Potato does not like to see
# "auto" option before "iface" for the first device specified.   
iface lo inet loopback
auto lo

auto eth0 
iface eth0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

thanks again for your help

---

### Post by thomasaaron on 2007-06-07
By the ifconfig output, your computer is not seeing a signal at all through your router.

1. From a terminal, enter:
sudo gedit /etc/network/interfaces

Put a # in front of EVERY line of that file except for these lines:

iface lo inet loopback
auto lo

Then Save the File. Reboot your computer.

2. Run ifconfig again. If it looks more like the following example (that is, it should display inet, bcast and mask addresses),  you should be able to connect to the Internet.

If it does not show inet, bcast, and mask addresses, you have a problem with your router and should try to reset it. Unplug, hold the reset button down for 60 seconds (for Linksys). Check your user's manual.

eth0      Link encap:Ethernet  HWaddr 00:17:31:99:85:95  
          inet addr:10.120.150.144  Bcast:10.120.150.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe99:8595/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7150857 (6.8 MiB)  TX bytes:1049001 (1.0 MiB)
          Interrupt:21 Base address:0x400 

eth1      Link encap:Ethernet  HWaddr 00:13:02:86:AC:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:7630 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 Memory:fe7ff000-fe7fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host




3. Do not use System > Administration > Network to connect to the Internet, it hoses the interfaces file.  Instead, you should be able to do all you need to do from the network icon in the upper right of your screen.

4. Avoid manual configuration if you can. Your router should be set to DHCP. Network Manager can do all the configuration work by itself. You should just be able to see the network and connect to it.

---

### Post by cward002 on 2007-06-07
Thanks thomasaaron. I will try these things tonight and let you know!!!!

---

### Post by cward002 on 2007-06-07
well that was not so good. I modified my interfaces file (cut and pasted) and then tried to connect both wired and wireless but no dice. I then tried to connect without the router as I had been doing but then that failed as well. I had to run pppoeconf from terminal to get my wired connection (without router). And here I am. I really appreciate this and I know you are probably more stumped than I am because I don't even know what to be stumped about LOL

---

### Post by cward002 on 2007-06-14
well I know that my wireless works at least because I can connect to wireless hot spots outside my home but just not to my home. I am sure it has to do with a bad cable or something. I will keep trying and post back.

---

### Post by thomasaaron on 2007-06-14
I've kind of lost track of this, and reviewing the thread left two quesitons:

1. Can you even SEE your WIRED access point using Network Manager?
2. Can you even SEE your WIRELESS access point using Network Manager?

If you CANNOT see your wired A.P., you either have a bad cable, a bad router, something is wrong with your router configuration, something is wrong with the way your modem and router are connected, etc...

If you CAN see your WIRED connection, but just can't connect to it, it is a configuration issue.

If you CANNOT see your WIRELESS connection, either your wireless radio (on your computer is not turned on) or you have a configuration or hardware problem with your wireless router.

If you CAN see your WIRELESS connection, but just can't connect to it, it is a configuration problem.

Can you please elaborate? (I know it's probably just me, but when these threads get beyond a page in length, I find it difficult to keep up with them.)

Best,
Tom

---

### Post by cward002 on 2007-06-15
No, it's not just you LOL. I am getting confused too. 

I recently purchased a Wireless Access point because I thought that the wireless router that I had was pooched(now I'm not sure)

the wireless access point only has a single port. I plug an ethernet cable from my modem into that port. the wireless radio is turned on ( at least the light is on when the computer boots)

Network manager sees the AP but when I choose that connection in Network manager and then try to get to any page(even the configuration page), firefox gives me the message saying it can't find the page.

I then tried to connect via my wired router. WAN Port connected to modem and then modem connected to LAN port on computer.I then run PPPOECONF which times out because it cannot find an interface (through my router)

I then connect directly from my modem to my computer and have to run PPPOECONF again to get a connection and here I am!!!

thanks Tom

Colin

---

### Post by thomasaaron on 2007-06-15
OK, let's deal with the wireless first.

Network manager sees the A/P. When you select it, does it give you a message saying that it is connected?

Give me the model of your router, and I'll try to download some documentation for it. Under feisty, Network Manager seems less...intuitive...in some ways. With some routers, it demands that Network Manager is configured EXACTLY the same as the router.

One other question, I just want to be clear on one other thing. Are you trying to get online via System > Administration > Network, or via Network Manager only (the little icon in the upper right of your screen that, when you click on it, graphically shows you all of the access points available)? I only ask because people sometimes get the two confused.

---

### Post by cward002 on 2007-06-15
Hi Tom.

The AP is a D-Link DWL7100AP. Iam trying to remember what happens when I select the network under NetworkManager. I think the access point sees the network and can connect to it but when I try to open a web page, it gives me the page cannot be displayed message. The same thing happens when I try to get to the AP config page at 192.168.0.50. I will confirm all this tonight and post back. 

Thanks Tom

Colin

---

### Post by cward002 on 2007-06-15
Hi Tom. 

I forgot to confirm that I only use NetworkManager to connect.

Thanks

Colin

---

### Post by thomasaaron on 2007-06-15
We've had several customers with D-Link routers that have struggled to connect. It is definitely a configuration problem.

Any D-Linkers out there that can help?

(I'll try to look up some info on it too)

---

### Post by organicveggie on 2007-06-17
The D-Link DWL7100AP is an *access point*, not a *router*.

[http://www.dlink.com/products/?pid=304]("http://www.dlink.com/products/?pid=304")

Here's a diagram that D-Link provides:

[http://www.dlink.com/products/resource.asp?pid=304&rid=1019&sec=0]("http://www.dlink.com/products/resource.asp?pid=304&rid=1019&sec=0")

Most wireless access points are merely conduits to the rest of the WAN and do not provide DHCP services, routing services, etc. That said, according the manual, the DWL7100AP *does* offer DHCP services and quite a few other features not normally found in an access point.

[ftp://ftp.dlink.com/Wireless/dwl7100AP/Manual/dwl7100AP_manual_06302005.zip]("ftp://ftp.dlink.com/Wireless/dwl7100AP/Manual/dwl7100AP_manual_06302005.zip")

However, the key thing the user said was that his DSL connection uses PPPoE. Unfortunately, as far as I can tell, the DWL7100AP does *NOT* support PPPoE. That feature is generally reserved for broadband routers like the Linksys WRT54G/GL and it's ilk. I'm not certain which D-Link wireless routers support PPPoE.

I personally use a Linksys WRT54GL with AT&T DSL service, which requires PPPoE. Your mileage may vary.

Hope that helps.

-Sean

---

### Post by cward002 on 2007-06-18
Hi Sean. 

This is what I was afraid of. I only found out that it was an access point after it was delivered!!! I bought it to replace another D-Link router(wired and wireless) that I think may be dead. when I try to use it, all the link lights on the front work but the power and status lights don't light up and I cannot connect. I tried typing PPPOECONF with the router(not the access point) connected but it can no longer see the connection(Same with the AP).

sounds like I may be buying another router or maybe just sticking with the wired connection at home and using the wireless on the road.


oh well

Thanks for your help

Colin

---

### Post by thomasaaron on 2007-06-18
Thanks, organicveggie.

---

### Post by cward002 on 2007-06-18
Yes thanks, Organicveggie

---

### Post by organicveggie on 2007-06-18
> **cward002 said:**
> Yes thanks, Organicveggie

No problem. Actually, I did the same thing myself a few years ago... I carefully bought a brand spanking new Linksys wireless router for myself, spent several hours trying to get it to work and finally realized I accidentally bought an access point instead of a router.

To add insult to injury, 6 months later while working at a very small startup company, I did the exact opposite. I *meant* to buy an access point for the office and bought wireless router instead. After several hours of trying to figure out why all the devices were appearing on a different network, I realized my mistake. *sigh*

So don't worry, you're not alone. :)

Fortunately for me, in both cases I knew someone who needed the exact device I bought by accident. I was able to sell off the virtually unused device at close to retail and buy the correct device. Might want to check with all of your friends/neighbors/relatives/etc. and see if anyone needs an access point. 

Or you may want to hold on to the wireless access point and use it to expand the coverage of your wireless network. I have a wireless router (Linksys WRT54GL) hooked up to my DSL modem, but due to the layout of my house and the position of the router, I don't get very good reception on my back deck... So I picked up a WAP54G access point and found a good spot for it such that it dramatically improved reception on the deck. Now I can sit outside, enjoy a nice cold one *and* use the laptop! 

Just something to keep in mind.

-OrganicVeggie

---

### Post by cward002 on 2007-06-19
Thanks for the story, organicveggie. At least I know I'm not alone !!! LOL

---

### Post by lewindha on 2007-06-19
Hello all

So I'm about to purchase one of Dell's Ubuntu Laptops.  I've never used wireless, but I'd like to set up a wireless network in my home.  A few sidenotes, I also have a windows PC, and an XBox 360(Couldn't wait for Sony any longer).  I want to be able to use all of them on a wireless network.  I know I can get the PC and 360 to work on most routers.  I'd like to get a gaming router.  So my question is:

Is there a list somewhere of wireless routers that we know works with Ubuntu?

Thanks

---

### Post by thomasaaron on 2007-06-19
lewindha, here is probably a better place to post your question:
[http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

This forum pertains to supporting System 76 computers.

Best,
Tom

---

### Post by lewindha on 2007-06-19
Sorry Tom,

I just saw that you were discussing DLink routers and access points.  The DLink gaming routers were suggested to me by a friend so I asked the question.  I'll post the question elsewhere.

Thanks
Eric

---

### Post by thomasaaron on 2007-06-19
Hi, Eric.

I see where you were going with it, now.
Your question was:

> Is there a list somewhere of wireless routers that we know works with Ubuntu?

So, I figured you were more likely to find the expertise you needed in the networking forum.

But if it is a D-Link router in particular that you want to know about, that is something we keep running up against around here.

Maybe organicveggie can help you out. :-)

Best,
Tom

---

### Post by cward002 on 2007-06-25
Hi Tom.

Well, there has been significant progress. I am now hooked up to a wireless router!!!!YAY!!!

However, whenever I want to switch from wired to wireless or vice versa, or when I turn off the computer, I lose the connection again and have to run sudo PPPOECONF to get it back which always works. However this messes up my interfaces file.

Also I cannot access the routers configuration page with either the wired or wireless connection.

But at least I am connected!!!

Thanks again for your help Tom

Colin

---

### Post by cward002 on 2007-06-26
Hi guys. 

I just re-discovered the link to the wireless page on the Ubuntu Wiki.

I am going to try going through tha to see if I can get my connection to behave properly. I will post back with any issues I encounter!!!

Thanks again for your help

Colin

---

### Post by cward002 on 2007-06-26
well I tried the stuff on the wiki but Iam still having to use PPPOECONF to get connected. I am attaching my two interfaces files. The first one is before I run PPPOECONF when I can't connect to wired or wireless. The second one is after I run PPPOECONF and I can connect to either wired or wireless

---

### Post by cward002 on 2007-07-03
I have a feeling that my problem is related to the fact this is a PPPOE connection because of he fact that I have to use PPPOECONF to connect at home (wired or wireless) but when I use the wireless externally, it finds the connection perfectly. When I am at home, Net work Manager finds the connection and connects but I cnnot get to any web pages, not even my router's setup page. This is using either the wired or wireless connection. I am just wondering whether iptables is somehow blocking the connection but I have never used Firestarter on this machine and so it just has the default iptables settings.

---


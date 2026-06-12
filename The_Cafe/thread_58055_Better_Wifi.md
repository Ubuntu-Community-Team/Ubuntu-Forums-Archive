---
title: "Better Wifi???"
date: 2005-08-18
forum: The Cafe
---

### Post by reckless2k2 on 2005-08-18
If any distro can do this, I would think it could be Ubuntu but I'm wondering how long before we can hope to see a zeroconfig wifi similar to Windows XP? 

* Auto-detect broadcasting networks and allow one click access to it

* Hold Wifi profiles and one click access

* Auto-detect your existing Wifi profiles and connect to known netowrk if found

I've tried several things (whereami, laptop-net, gtkwifi...etc..etc..) with little luck. I currently run a script off of Kwifi after KDE startup to connect to "known" networks. 

I know there can be a better way. 

If Windows can do it........Ubuntu can do it just as good if not better!!!

---

### Post by TheDude on 2005-08-18
Drivers are a big problem with wirelessness. Ndiswrapper is not the best solution.

---

### Post by Brunellus on 2005-08-18
1) Please read the general "why can't it be Windows" [disclaimer]("http://www.ubuntuforums.org/showpost.php?p=307823&postcount=1") posted by aysiu.

2) The problem is not entirely in the hands of the Ubuntu community, nor that of Linux as a whole.  Those chips need drivers--bits of software that actually tell the OS's kernel how to address the hardware to make it work as intended.  As you might imagine, this is rather tricky code, and most device manufacturers hide it.  They provide drivers that only work with Windows, and refuse to disclose specifications or source code with anyone.

There are workarounds.  Ndiswrapper is a program that 'wraps' around the Windows driver and makes it work with the linux kernel.  This program is under heavy development, and it may or may not work with the driver/card/chipset combination that you use in Windows.  Also, it is not very n00b-friendly, sadly.

Free and Open-source drivers would be preferable.  But, absent the cooperation of device manufacturers, these are very hard to write.  The developers have to reverse-engineer the card and the driver, with unpredictable results.  It's like trying to build a locomotive only by looking at photographs of locomotives--it's possible, but not easy, and your locomotive might not be 100 percent like the locomotive in the photograph.

---

### Post by allans on 2005-08-18
[QUOTE=reckless2k2]If any distro can do this, I would think it could be Ubuntu but I'm wondering how long before we can hope to see a zeroconfig wifi similar to Windows XP?[/QUOTE]

Does windows xp fully support zeroconf?  I thought that os x was the only os with it fully implemented, please correct me if I'm wrong though.

As for the driver problem, my solution was to by a wireless access point, basically a box that provides full wireless capabilities that is connected to my pc by an ethernet cable, the only disadvantage being that I can't tell exactly how fast the wireless network is operating at, and I need a seperate power supply for the access point.

Allan

---

### Post by poofyhairguy on 2005-08-19
[QUOTE=allans]
As for the driver problem, my solution was to by a wireless access point, basically a box that provides full wireless capabilities that is connected to my pc by an ethernet cable, the only disadvantage being that I can't tell exactly how fast the wireless network is operating at, and I need a seperate power supply for the access point.[/QUOTE]

Mmmm. That sounds tasty.

---

### Post by Brunellus on 2005-08-19
[QUOTE=poofyhairguy]Mmmm. That sounds tasty.[/QUOTE]
 Tasty and pricey.  I priced one of these back when I was considering this...and in the end, I rolled up my sleeves and learned how to make ndiswrapper work.

Self-reliance and common humanity.  If Ralph Waldo Emerson had an OS, it would be Linux for sure.

---

### Post by allans on 2005-08-19
[QUOTE=poofyhairguy]Mmmm. That sounds tasty.[/QUOTE]

Oh yeah...hopefully only a temp solution.  Was the same price as a wireless card over here though, could have been worse.

Allan

---

### Post by zsazs on 2005-12-08
This isn't a driver problem.  This hypothetical application would just really be a frontend to iwconfig/ifup that could scan for available networks and connect to predefined ones.  I've found that waproamd, or wpa_supplicant in combination with ifplugd, can do this.  They're daemons that go about their business silently, though.  I must admit that XP's "zeroconfig" is pretty nice, and something similar, if not better, would be quite a boon to wireless users.

Note that Microsoft's term "zeroconfig" or "zeroconf" applies to this type of wireless network scanning, and not Apple's Bonjour.

---

### Post by lerrup on 2005-12-08
My understanding of the first post is that he is not complaining about drivers -and I would agree with what he wants.

Ubuntu has always been excellent at working my wireless card (in a centrino notebook).  However, scanning for networks and even connecting to a known network when there has been a brief outage has been really pants.

I have tried a number of things with no luck so far.  So, a scanning and connecting procedure would be a must in my opinion for linux.

---

### Post by lleb on 2005-12-08
[QUOTE=lerrup]My understanding of the first post is that he is not complaining about drivers -and I would agree with what he wants.

Ubuntu has always been excellent at working my wireless card (in a centrino notebook).  However, scanning for networks and even connecting to a known network when there has been a brief outage has been really pants.

I have tried a number of things with no luck so far.  So, a scanning and connecting procedure would be a must in my opinion for linux.[/QUOTE]


add to that something in the background that is constantly monitoring all avaliable networks both in the wifi world and wired to make reconnects faster and easier on the user.

i agree the ndiswrapper is a major PITA.  first you have to hope it will work, and if it does you have to hope it will not crash your system.

drivers are a major problem, that is why i have made it a point to first check what chipsets work in linux WITHOUT ndiswrapper, and buy only those brands, while sending e-mails to the other brands requesting native linux drivers.

---

### Post by ssam on 2005-12-08
if you have a chipset with a good driver then network-manager does most of what you want.

however it plays around with the dns system a bit (installs a local dns server), so if you get problems they can be a pain to sort out.

when its working its very good though. it can store the keys and options for each acess point you use. and it will give you a list of available access points

---

### Post by Rinzwind on 2005-12-08
I don't exactly understand it.

I've got kWifiManager running. How's using that a problem? 
When I use 'scan for networks' it pops up with a message 'available networks'. 
Mind you I only see my own one cuz there's not alot of wifi-users here (1...) so I -think- it should also show me other wifi-networks when I go elsewhere (?)

Doesn't that do what TS is asking? 
Or am I wrong in assuming it will show me all available networks(?)

---

### Post by prizrak on 2005-12-09
Actually my biggest problem isn't even the fact that it doesn't auto connect to preferred networks (which would be real nice). The most annoying part is that the OS expects the same SSID on bootup which can be a major PITA since wireless users do tend to move between different networks. So when the OS boots I have to go into the network and have to change the settings. At the very least I'd like a prompt on boot that gives me a list of networks to connect to. Also there really needs to be native WPA support unecrypted wi-fi is not a very good thing, and 128bit WEP can be cracked in about an hour.

---

### Post by reckless2k2 on 2006-01-19
WPA, 64bit WEP, and 128bit WEP can all be "cracked" in much shorter amount of time than an hour. If you have a "weak" key, the exploit could take as little as 3 minutes. 

While security is and should be a concern, detect and connect needs to be more XP'ish with multiple profiles or even with internet cafe connection.

---

### Post by reckless2k2 on 2006-01-19
And my OG post was never about drivers especially since I have a builtin Atheros chipset which has full support in Linux. I have and use OSX (Jaguar, Panther, Tiger) and there is not a zeroconf solution similar to XP. Drivers or not, there should be a builtin program that can scan, detect, connect once a driver is or can be identified more easily. If the driver support is existing, which in this case it is, the connection response is my issue. Thanks for those that picked up on that in earlier posts. 

I have no problem with mucking around in the terminal but I want to "sell" the product to Windows converts and better wifi is at the top of the list since most of those I try to convert only need access to internet, email, & IM. Terminal switching around /etc/network/interfaces or scripting ESSIDS is not easily appealing to converts.

---

### Post by stimpack on 2006-01-19
Agreed better wifi is badly needed, simple clicks to choose a network and connect (WPA essential!), my laptop is still Windows and poor wifi is the only reason why.

---

### Post by prizrak on 2006-01-19
The new Network-Manager (will be in Dapper AFAIK) works just like Wireless Zero. My biggest issue now is WPA if I switch to an unsecured network I have to shut down the supplicant daemon and restart networking. According to wpa supplicant's website it's supposed to come with wpa_gui that seems to allow management of multiple networks in a wireless zero kind of way but it's not included in the one that can be gotten from the repos. There is a CLI interface but I haven't figured it out yet. 
I think the wi-fi issues come from Linux being mostly a server OS where there is little need to network hop. Windows and OS X on the other hand were designed to support wi-fi from the beginning and also for laptops before that to make network hopping easier. Gtk-wifi and wifi-radar never worked for me for some inexplicable reason, my card is atheros based and fully supported so I dunno does get pretty annoying.

---

### Post by cbudden on 2006-02-23
I have had the annoying DNS problem with network manager, aswell as it not re connecting upon resume from hibernate.  If GTK-wifi supported WPA and more config options for each network such as DNS, static IP, default route etc it would be a very good app to use.

---

### Post by prizrak on 2006-02-23
It seems like WPA_GUI takes care of all of that but for some reason Ubuntu's wpa_supplicant does not include it.......

---

### Post by Protostar on 2006-02-23
[QUOTE=prizrak]Actually my biggest problem isn't even the fact that it doesn't auto connect to preferred networks (which would be real nice). The most annoying part is that the OS expects the same SSID on bootup which can be a major PITA since wireless users do tend to move between different networks. So when the OS boots I have to go into the network and have to change the settings. At the very least I'd like a prompt on boot that gives me a list of networks to connect to. Also there really needs to be native WPA support unecrypted wi-fi is not a very good thing, and 128bit WEP can be cracked in about an hour.[/QUOTE]

That's the problem I have as well. It takes forever to boot because it is trying to connect to my campus's wireless network. I also would like an option where Ubuntu defaults to the wired connection once it senses its presence. That would be REALLY helpful.

---

### Post by prizrak on 2006-02-23
[QUOTE=Protostar]That's the problem I have as well. It takes forever to boot because it is trying to connect to my campus's wireless network. I also would like an option where Ubuntu defaults to the wired connection once it senses its presence. That would be REALLY helpful.[/QUOTE]
You can hit Ctrl+C while it's bringing the network up to skip it.

---

### Post by direwolf on 2006-02-24
Although XP's zeroconf is fairly good at it, it does have some of its own problems; not to mention that it's XP in the first place. 

I understand the OP's dilemma. Apparently, so does at least one kernel developer, an HP Wireless Extensions developer and an ISC DHCP spokesperson.

[http://www.internetnews.com/dev-news/article.php/3586801](http://www.internetnews.com/dev-news/article.php/3586801)

You would think that the new dhcp client he speaks of should be able to do this (find x/new network, connect to it automagically) but I tend to agree with his detractors that writing an entirely new dhcp client _may_ cause more problems than it solves. Either way, this problem/idea has caught on and should be sorted in due time.

---

### Post by benplaut on 2006-02-24
I've given up. I have several icons on a hidden panel (kinda... this is e17), and i just click on one to connect to a certain network. It's just plain faster.

---


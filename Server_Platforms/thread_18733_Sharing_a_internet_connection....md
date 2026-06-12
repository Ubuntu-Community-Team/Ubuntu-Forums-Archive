---
title: "Sharing a internet connection..."
date: 2005-03-08
forum: Server Platforms
---

### Post by Malroy on 2005-03-08
HI folks,

I have a problem... I want to share a internet connection, i have i-net from cable tv. In my home i have to pc computers - the cable modem is connected to the computer with ubuntu instaled through 3com ethernet card -  second computer is connected to ubuntu computer throught second card realtek.  On ubuntu computer I have internet, and i want to share it with second computer. I have instaled Firestarter, and chose in option share internet connection by dhcp - but i haven't dhcp server on ubuntu. Can you tell me how can I start dhcp server, and how can I configure that server to make possible sharing a internet conneciton throught Firestarter.

Maybe ther is another way to sharing connectio - pls let me know if it is...

Thanx for your answers

Malroy

PS: Sorry for my terrible english, I have hope that somebody understand me :)

---

### Post by az on 2005-03-08
You need masquerading.  It is also called NAT, network address translation.


I never used firestarter.  Packages that do what you need are ipmasq and dnsmasq.  Dnsmasq includes a great dhcp server.

Shorewall will also do NAT an dyou can add some firewalling.

---

### Post by dewey on 2005-03-08
Why don't you just go out and purchase a cheap router, they run about $30-40 when not on sale, and make everything very simple.  All you have to do, is plug your cable modem into the router, and each computer into it. It also allows for quick addition of new computers.(Assuming it's a home router, which has multiple ethernet ports for switching, and not a $2,500 Cisco router.)

Something as simple as
[http://www.bestbuy.com/site/olspage.jsp?skuId=4625347&type=product&productCategoryId=cat01029&id=1051384470326](http://www.bestbuy.com/site/olspage.jsp?skuId=4625347&type=product&productCategoryId=cat01029&id=1051384470326)

Would do, but I'm sure you could find it cheaper, I just did a quick search on bestbuy.com.  I hate to tell people to go and buy something to make it easier, but it will really help.

---

### Post by Malroy on 2005-03-09
[QUOTE=dewey]
Would do, but I'm sure you could find it cheaper, I just did a quick search on bestbuy.com.  I hate to tell people to go and buy something to make it easier, but it will really help.[/QUOTE]


Thx for your sugestion, I thin I do it. Anyway knowledge about sharing connection is good to knowing. 


My english - even I do not understand myself ;)

---

### Post by Jad on 2005-03-09
This may help
[http://ubuntuforums.org/showthread.php?t=17131](http://ubuntuforums.org/showthread.php?t=17131)

PS: whats your native language?

---

### Post by Malroy on 2005-03-09
[QUOTE=Jad]
PS: whats your native language?[/QUOTE]

polish :) 

I just have started to learn english...

---

### Post by machiner on 2005-03-12
The simplest way to let 2 (or more) computers share a connection it to use a simple hub.

I bought a used Netgear 8 port DS108 for 10 bucks and it's terrific.

I plug my DSL (it's a cat-5 cable) right into the hub and then I plug each box into the hub as well.

Couldn't be simpler. Now I can write insane toaster-oven stories on this forum and my kids can surf the kid's sites.

I've got 2 nicks in my box so I suppose I can set up a typical LAN here, but why bother?

Good luck.

---

### Post by darkoptix on 2005-03-12
You could make a router out of a old POS comp that cannot run ubuntu... 
[http://www.freesco.org](http://www.freesco.org)
I'm using it right now for a dialup router, works great.

---

### Post by az on 2005-03-13
I run Ubuntu on three POS (pentium 133) computers.

---

### Post by dankurth on 2005-03-13
Here's what I did to get internet connection sharing to work after installing ubuntu 4.10. My external connection is cable modem with dynamically assigned address and internal machines are windows (win98 and xp). Hope this helps you as well.

First set the internal and external ethernet cards. 

added eth0 as internal interface by running network-admin. Settings are:
Activate when the computer starts=check
ip address=192.168.0.1
subnet mask=255.255.255.0
gateway address=

note: I did NOT set gateway but left blank intentionally so that it will use default external dynamically assigned gw.

eth1 settings are:
Activate when the computer starts=check
Configuration=Automatic(DHCP)

note: eth1 was chosen as the external interface during installation. DNS settings were added by installation script automatically. ps...since eth1 was found by the script as being my slower external card I found that I had to drop it in the settings and then re-add both in order to set eth0, otherwise adding an interface gave me eth2 which did not correlate to a device.

Booted up a win98 machine (previously configured to use 192.168.0.1 as both internet gateway and nameserver).

Installed package bind9 in order to get names daemon. 

Installed package dhcp3-server and told it during init script to listen for dhcp requests on eth0 (the internal interface).

Added following lines to /etc/dhcp3/dhcpd.conf:
subnet 192.168.0.0 netmask 255.255.255.0 {
   range 192.168.0.2 192.168.0.10;
   option broadcast-address 192.168.0.255;
   option routers 192.168.0.1;
}


Started dhcp3-server: 
/etc/init.d/dhcp3-server start

Ran:
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

Rebooted win98 machine and was then able to browse internet from windows.

---

### Post by jdonnell on 2005-03-14
[QUOTE=machiner]
I plug my DSL (it's a cat-5 cable) right into the hub and then I plug each box into the hub as well.
[/QUOTE]

Are you sure it's a hub and not a router? Something has to translate multiple internal ip addresses to your single external ip address and a hub won't do it. Maybe your dsl router does, but I'm not sure if most do.

---

### Post by kianziack on 2005-09-20
i'm having trouble with my network... what i want is to share my internet connection from my pc to other pc... i can ping the dns and ip add but still i can't browse... any one care to teach me how to make it work... ohh one thing every time i open my network properties there's alwasy a pop up say's "your DHCP is not supported and then there's an option and i chose hoary.. but still it wont work.. by the way im using kubuntu... plz somebody teach i'm noob bout linux beacuse this is the frist time i configure linux T_T i think i'm gonna crazy  ](*,)

---


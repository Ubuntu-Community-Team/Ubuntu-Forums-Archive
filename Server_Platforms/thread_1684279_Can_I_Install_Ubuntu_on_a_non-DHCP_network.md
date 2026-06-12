---
title: "Can I Install Ubuntu on a non-DHCP network"
date: 2011-02-08
forum: Server Platforms
---

### Post by ApacheOmega on 2011-02-08
I'm trying to install Ubuntu server on an older 05-06 Desktop (IBM) and when I get to the Configuration part it stops right around 95% and the prompt reads that configuration failed do to the fact that my unit is running a non DHCP Network or my machine is two slow. Now it does only have 1 gig in it right now so I'm thinking that might be the problem also. But if it is a DHCP issue how can I install UBUNTU or is it even possible?

Thank You!!!

---

### Post by slooksterpsv on 2011-02-08
> **ApacheOmega said:**
> I'm trying to install Ubuntu server on an older 05-06 Desktop (IBM) and when I get to the Configuration part it stops right around 95% and the prompt reads that configuration failed do to the fact that my unit is running a non DHCP Network or my machine is two slow. Now it does only have 1 gig in it right now so I'm thinking that might be the problem also. But if it is a DHCP issue how can I install UBUNTU or is it even possible?

Thank You!!!

Leave it disconnected from your network. Don't connect any ethernet cables or that. If it still happens, it could be an issue with the disc. I've installed server without a network connection. What version? 10.04 or 10.10 or other?

---

### Post by ApacheOmega on 2011-02-08
it's 10.10 I guess I know it's the latest version - so I should just look up my IP address or are you saying I have to be plugged into the internet in order to config. my server and P.C. - I'm not to Keen on how this works - could you give me some pointers? how do I install manually?

---

### Post by ApacheOmega on 2011-02-08
I get it- I should set everything up instead of configuration and leave that machine on hooked from the internet.

---

### Post by Mr Mookie on 2011-02-08
Like he said.. try the install "without" a cable plugged in first. Then once you are up then connect it.

---

### Post by ApacheOmega on 2011-02-09
OK I'm having problems again at the Select and Install software point of the menu should I not select automatic updates right now and just stay manual for now?

also - 
should I select all or any of the predefined collections of software ( DNS Server, LAMP, MAIL server, etc.) and if I don't select any of them how do I go back and install them for later?

---

### Post by ephmanjmm on 2011-02-09
To get back to the options use:

sudo tasksel

I choose manual for the updates as I want to know when and what is going to be updated. I am certain others have different opinions on these matters.

---

### Post by ApacheOmega on 2011-02-09
OK I got the basics installed except LAMP and all the extra bells and whistles so How do I go back and get all that installed and why would it not install it from the go and is this the point I should go back and configure my network?

also I loaded the server without an operating system s that a bad thing and how do I go back and infuse it with an OS of my choice and what would be the best OS to Run with UBUNTU SERVER?

---

### Post by volkswagner on 2011-02-09
> **ApacheOmega said:**
> OK I got the basics installed except LAMP and all the extra bells and whistles so How do I go back and get all that installed and why would it not install it from the go and is this the point I should go back and configure my network?

also I loaded the server without an operating system s that a bad thing and how do I go back and infuse it with an OS of my choice and what would be the best OS to Run with UBUNTU SERVER?

Before spending time configuring and adding software, get the network card working.

Ubuntu Server 10.10 is the operating system, so I'm not sure what you mean "loaded without an operating system".

To get the network up and running you can edit /etc/network/interfaces file.  You will need the specifics on your local network.

You will need to know how your network card is recognized eth0, eth1 or otherwise.

Issue the following to see if you network card is listed.
```
ifconfig
```

Use the information from above and edit interfaces file.
```
sudo nano /etc/network/interfaces
```

```
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
```

Obviously the numbers above will need to match your LAN.

Save file and restart networking.

```
sudo /etc/init.d/networking restart
```

check if you have net with host.

```
host google.com
```

If it returns with googles dns ip's your good to go.

You can then start adding packages and update.

```
sudo apt-get update
```

```
sudo tasksel
```

---

### Post by ApacheOmega on 2011-02-09
what I mean by No OS is the start up says no OS detected I thought that would be some kind of problem. 

another thing is that its all command line in which I'm seriously not familiar with but willing to learn what ever it takes.

I'll try the steps listed and if theres any problems I get back w/you 

P.s.  I must be seriously doing this wrong cause learning all this new stuff is difficult but worth it

---

### Post by ApacheOmega on 2011-02-09
Ok I'm trying to get my network running now and I'm at the screen that reads at the top (GNU nano 2.2.4         file:/etc/network/interfaces)
on the screeen line 1 reads
#This file describes the network interfaces available on your system
Line 2
#The loopback interface
auto lo
iface lo inet loopback


then below all this at the bottom of the page has a menu that reads
^G Get Help   ^O WriteOut   ^R Read File   ^Y Prev Page   ^k Cyt Text      ^C Cur Pos
^X Exit          ^J Justify        ^W where is   ^V Next Page   ^U UnCut Text  ^T To Spell

What do I do with all this cause I was just trying to get the numbers adn configuration off of my interface so I can config.

I try to open something off the menu below and nothing happens (probably because I'm hitting the wrong key strokes) but what do I do here?

---

### Post by egpetrich on 2011-02-09
I think you have jumped ahead too far. The description you give tells me that you are editing /etc/network/interfaces. If you don't already know your network interface name and what address you want to provide, this file won't help you.

The lines at the bottom of the screen give you reminders of commonly-used editing commands. To exit from the nano editor, press ctrl-X. (The program may ask you if you really want to exit. Respond with a "y", I think.)

First order of business: What do you see when you enter the command "ifconfig"?

---

### Post by Iowan on 2011-02-09
**nano** takes a li'l getting used to... ( I like it, cuz the shortcuts are listed).  The "^" means CTRL. You *should* be able to either hand-enter the information below the existing text - or (preferably) copy/paste it in. CTRL-O should save it. CTRL-X will exit.

---

### Post by ApacheOmega on 2011-02-09
When i hit ifconfig:
Link encap:local loopback
inet addr:"          "    Mask:"            "
inet6 addr:  ::          Scope host
up loopback running MTU: "  "       Metric:
Rx Packets
Tx Packets


Of course I left out the digits but you can imagine what in there but no errors came up or anything.

should I have my ethernet connection plugged in while I'm doing this?

---

### Post by ApacheOmega on 2011-02-09
ok when i put in host google.com
it reads :: connection timed out; no servers could be reached

What am i doing wrong now?

---

### Post by volkswagner on 2011-02-09
I don't see the network card on the output of ifconfig.

What is the output (network related only) for

```
lspci
```

I assumed your network card was recognized because you were warned about not having a DHCP server.  Is it true, your network does not have DHCP?  Do all machines on the network have static assigned ip addresses?

You will want to start here, since your NIC is not listed, most likely it is not recognized by the system.  You may need to manually load the drivers.

---


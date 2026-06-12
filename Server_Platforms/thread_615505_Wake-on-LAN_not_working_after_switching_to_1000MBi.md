---
title: "Wake-on-LAN not working after switching to 1000MBit"
date: 2007-11-17
forum: Server Platforms
---

### Post by RunningDeath on 2007-11-17
Hi all,

I have a strange behavior I would like your opinion and help on.

My Wake-On-Lan is all setup and working in a 100MBit environment. Now I bought a new 1000MBit switch, installed it and all of the sudden WOL doesn't work anymore.

I am very sure it is not a switch problem because the server starts when it is connected to the 100MBit switch and the client is connected to the 1000 MBit switch, but as soon as my server is connected to the 1000 MBit switch it stops working.

Does anybody have an idea what the reason could be ?

One difference between the connection is that 100Mbit is half duplex vs. 1000Mbit which is full duplex.

I have:
[FONT="Courier New"]>uname-r
2.6.20-15-server

>lspci | grep Ethernet
01:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

>ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000037 (55)
        Link detected: yes
[/FONT]

Thanks
Stephan

---

### Post by James79 on 2007-11-18
Is it possible that something is filtering out the [WOL magic packet]("http://en.wikipedia.org/wiki/Wake_on_lan#Magic_Packet")? Or regulating UDP traffic in general etc..

---

### Post by RunningDeath on 2007-11-18
Hi,

thanks for the answer. I tried some more using this command when the server is up.
nc -l  -p 9 -u

and the packet is actually received. So I think it is either the BIOS or the driver of the network card.

Do you know how I can find out which one is more likely to cause the problem ? or maybe a completely different idea ?

Thanks !

Stephan

---

### Post by James79 on 2007-11-19
Well the simplest reason for a computer not waking up after receiving a WOL packet is simply because it is not listening!

In linux, you have to "manually rearm" the nic to listen for it (the WOL packet) everytime you turn off the computer. Obviously this is best placed in a startup/shutdown script etc...

Also, yes, this feature must be enabled in the BIOS as well. I'm assuming you've configured both of these properly if as you say it used to work...?

Just to be sure, *when your computer is off*, do you see a light on your network card? Most (?) NICs do this to indicate that they are indeed active and ready to be sent a WOL packet.

If in fact your computer is properly setup, and all you did was swap the switch, then my initial guess is still the most likely - that it's somehow filtering it. Is this indeed the case? That we're talking about the exact same machine, and only the switch in the middle of the network was changed?

---

### Post by RunningDeath on 2007-11-19
Hey,

thanks for the answer. Yes I did all those things ;-) and the ONLY change in my network is the new switch.

To answer your questions.
* The light is one when the computer is off
* Ubuntu is modified to listen to the WOL packet and I do this every time the server boots.

> If in fact your computer is properly setup, and all you did was swap the switch, then my initial guess is still the most likely - that it's somehow filtering it. Is this indeed the case? That we're talking about the exact same machine, and only the switch in the middle of the network was changed?
Yes exactly, only the switch, and I think it is not filtered because if I send the packet when the server is live the packet is being received as I indicated in my previous post.

Hope you have any tips that might bring me forward.

Thanks
Stephan

---

### Post by James79 on 2007-11-19
Do other computers on the same switch have the same problem? Have you tried?

---

### Post by RunningDeath on 2007-11-19
not yet,

but a good suggestion. Will try tomorrow. Keep you posted

---


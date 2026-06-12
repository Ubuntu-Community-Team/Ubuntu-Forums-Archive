---
title: "Power options for Ubuntu 14.04 LTS"
date: 2016-01-09
forum: Server Platforms
---

### Post by Mike_Ramsey on 2016-01-09
Greetings all~
I am trying to lower my power consumption in general. I currently have a Dell Poweredge 2900 running Ubuntu 14.04 Server. I use it for a fileshare but also as a web server for my personal use. My problem is that it pulls a good 330watts 24/7.

Is it possible to hibernate the machine and wake it on network traffic? I have looked in the bios and there is no option to power on at a given time so that ruled out a shutdown script pretty quick. Thus my question of a sleep state or hibernation.

I have been googling around but haven't found what I am looking for, likely just not asking the right way.

---

### Post by matt_symes on 2016-01-09
Hi

> **Mike_Ramsey said:**
> Greetings all~
I am trying to lower my power consumption in general. I currently have a Dell Poweredge 2900 running Ubuntu 14.04 Server. I use it for a fileshare but also as a web server for my personal use. My problem is that it pulls a good 330watts 24/7.

Is it possible to hibernate the machine and wake it on network traffic? I have looked in the bios and there is no option to power on at a given time so that ruled out a shutdown script pretty quick. Thus my question of a sleep state or hibernation.

I have been googling around but haven't found what I am looking for, likely just not asking the right way.

Have you looked into WOL (Wake on Lan). 

I use it on my backup server to wake it up when i backup my laptop and other computers.

Look in your BIOS and see if there is an option to enable it.

You'll also need a network card that supports it. Many have this. You can check using ethtool.

If it's not already installed then install it using...

```
sudo apt-get install ethtool
```

Then check your network card. Change "<ethernet_interface>" below as required.

```
sudo ethtool <ethernet_interface> | grep -i wake
```

You'll be looking for the "g" option. This is the "WOL using a magic packet" option.

Here is an example from my laptop. You'll want to see something similar on your server.
```

matthew-xu-16-04:/home/matthew:0 % sudo ethtool enp3s0 | grep -i wake
        Supports Wake-on: pua**[COLOR="#FF0000"]g[/COLOR]**
        Wake-on: g
matthew-xu-16-04:/home/matthew:0 
```

You can then enable the "g" option on the network card if it's not enabled 

```
sudo ethtool -s <ethernet_interface> wol g
```

and wake the computer from a different PC using wakeonlan.

Install wakeonlan on the other PC if it's not installed.

```
sudo apt-get install wakeonlan
```

and to wake your server...

```
wakeonlan <MAC address of network card on server>
```

I power down my server (but not physically switch it off or unplug it) and wake it up from my laptop or one of my other computers, so my backup server draws next to no power until i need it. 

If your BIOS and network card supports this then there is no need to suspend or hibernate. You can just power down as you normally would.

If you need more information then post back.

Kind regards

---

### Post by Mike_Ramsey on 2016-01-09
> **matt_symes said:**
> 

If you need more information then post back.

Kind regards

Thanks Matt this is a good start. I have since convinced myself that I don't believe my hardware is capable of a sleep state so this is likely my only option.

---

### Post by matt_symes on 2016-01-09
Hi

> **Mike_Ramsey said:**
> Thanks Matt this is a good start. I have since convinced myself that I don't believe my hardware is capable of a sleep state so this is likely my only option.

When looking in your BIOS, WOL might not be called something obvious (and useful) like 'Wake on LAN'.

It may be a power management event called something like 'power on by pci' or something else really, really useless like that.

My point is, if you don't see an obvious option then look for something that may not seem in any way obvious. Get a copy of the BIOS manual if you can.

I really think that, half the time, BIOS writers are swigging whisky at their work stations while they work :)

Kind regards

---

### Post by tgalati4 on 2016-01-09
I use WoL on my PowerEdge 1750's.  They run 200 to 240 watts, so I only wake them when I need to do some development work.  I use RaspberryPi's for 24/7 service--only a few watts of power.  I'm pretty sure the 2900's will support WoL, but you will have to hack at it.  On mine, I had to enable WoL using a script put in /etc/rc.local because the network card did not keep the "g" setting between power outages.  Not a frequent Use Case, but enough to be annoying.

The real reason for global warming is that companies keep building server farms in northern latitudes to save on cooling costs.

---

### Post by Mike_Ramsey on 2016-01-10
> **tgalati4 said:**
> I use WoL on my PowerEdge 1750's.  They run 200 to 240 watts, so I only wake them when I need to do some development work.  I use RaspberryPi's for 24/7 service--only a few watts of power.  I'm pretty sure the 2900's will support WoL, but you will have to hack at it.  On mine, I had to enable WoL using a script put in /etc/rc.local because the network card did not keep the "g" setting between power outages.  Not a frequent Use Case, but enough to be annoying.

The real reason for global warming is that companies keep building server farms in northern latitudes to save on cooling costs.

I managed to get WOL enabled on the 2900. Ran powerdown via ssh and sent the WOL packet from my router and it worked. This is my home server and we do samba shares and I run a private web server for playing around. My first choice would have been to have the machine sleep and wake up on network traffic. My next step will be to run a script to run the send the wake packet at a specified time like 8:00 AM and a powerdown script at 10:00PM.

Also when I tried to hibernate I think Ubuntu went into a hibernate state but the machine never really powered down. fans were still running etc.

---

### Post by matt_symes on 2016-01-10
Hi

> **Mike_Ramsey said:**
> I managed to get WOL enabled on the 2900. Ran powerdown via ssh and sent the WOL packet from my router and it worked. This is my home server and we do samba shares and I run a private web server for playing around. 

Excellent ! You're mostly there then :)

> My first choice would have been to have the machine sleep and wake up on network traffic.

Seriously ? Then every broadcast packet would wake the machine up such as ARP broadcast packets.

> My next step will be to run a script to run the send the wake packet at a specified time like 8:00 AM and a powerdown script at 10:00PM.

If you need help with this then just say the word.
> 
Also when I tried to hibernate I think Ubuntu went into a hibernate state but the machine never really powered down. fans were still running etc. 

I don't own one so i can't really help but maybe tgalati4 may have some suggestions for you.

Kind regards

---

### Post by Mike_Ramsey on 2016-01-10
> **matt_symes said:**
> Hi



Excellent ! You're mostly there then :)



Seriously ? Then every broadcast packet would wake the machine up such as ARP broadcast packets.



If you need help with this then just say the word.


I don't own one so i can't really help but maybe tgalati4 may have some suggestions for you.

Kind regards

Well maybe I phrased that wrong. I guess what I really meant was to wake it up from a sleep state via WOL instead of powering completely down. pm-suspend-hybrid seemed to work with the exception of the physical machine powering down. I am just not sure how to determine how to test the hardware to see if it is capable. Being that it is a true server though it is doubtful. With that said a powerdown script is the next best bet.

---

### Post by matt_symes on 2016-01-10
Hi

> **Mike_Ramsey said:**
> Well maybe I phrased that wrong. I guess what I really meant was to wake it up from a sleep state via WOL instead of powering completely down.

That makes more sense :)

> pm-suspend-hybrid seemed to work with the exception of the physical machine powering down. I am just not sure how to determine how to test the hardware to see if it is capable. Being that it is a true server though it is doubtful.

Hopefully someone will know and be able to tell you one way or another.

> With that said a powerdown script is the next best bet.

Now that i may be able to help you with if you do need a hand. 

It sounds like you use case is pretty simple though and you sound like you know what you're doing.

Kind regards

---

### Post by Bucky Ball on 2016-01-10
Good suggestions on the hardware side, and certainly wake-on-LAN is a way to save power, but another is to use an 85+ certified power supply for when the machine is actually on, and one that is rated to what you have in the box. 

You say you rig pulls 330W? What size PSU are you using? Is it a 700W generic silver box? Replace it and start saving immediately. :)

Just throwing that in.

---

### Post by Mike_Ramsey on 2016-01-10
> **Bucky Ball said:**
> Good suggestions on the hardware side, and certainly wake-on-LAN is a way to save power, but another is to use an 85+ certified power supply for when the machine is actually on, and one that is rated to what you have in the box. 

You say you rig pulls 330W? What size PSU are you using? Is it a 700W generic silver box? Replace it and start saving immediately. :)

Just throwing that in.

Hehe it actually has redundant dual 930watt PSU's. I can cut about 30 watts just by removing one of them. It has dual Xeon 2.0 Ghz 5130 processors.  16GB of Ram, 1 SSD for the OS and 4 platter drives for 4.5 TB of storage. I have been searching all around to figure out how to put it in a sleep state. When it hibernated it did drop power to a point but the fans were still 100% and it was pulling around 35 watts less. I'd be real happy if I could maintain a sleep state at ~50watts.

---

### Post by matt_symes on 2016-01-10
Hi

> **Bucky Ball said:**
> Good suggestions on the hardware side, and certainly wake-on-LAN is a way to save power, but another is to use an 85+ certified power supply for when the machine is actually on, and one that is rated to what you have in the box. 

You say you rig pulls 330W? What size PSU are you using? Is it a 700W generic silver box? Replace it and start saving immediately. :)

Just throwing that in.

If you want some hardware suggestions, then i have some.

I have to agree with an 85+ power supply. That'll make a big difference instantly. I have an evga gold rated power supply in my media server for this exact reason.

If your hard drive support it, then spin them down when not in use. You can use the *hdparm* command to do this. This can save power.

I don't know about Xeons as they are designed for servers specifically, but standard Intel chips can be down clocked. You can run the powersave governor to ensure the chip runs at the lowest clock speed. I do this on my media server and change to the ondemand governer when i want to to something requiring more CPU grunt such as spinning up a VM.

You can also power down any bus devices you're not using by poking values into /sys/bus/pci/devices/<.......>/powerdown.

Disable or remove any unused services. This lower the number of times your CPU needs to come out a sleep state. Once again, I'm not sure if this is applicable to Xeons but it may be worth investigating.

You've made a realise that i don't know enough about Xeons and need to read up more :)

Kind regards

---

### Post by MAFoElffen on 2016-01-10
I have 3 Dell PowerEdge 2900 Gen III's...

Do you have single or redundant PSU's? Mine are redundant (2 each). I feel you. 

To thers that who spoke mentioning 250W and 330W PSU's ... The PSU's are 930W each. It's an Enterprise class server with 2 x 4-core Xeons, capacity for internal drives is 8 hot-swaps in the main bays, 2 more if you have the optional flex-bay.(Mine do) Takes SATA or SAS 6GB/s drives, but is limited to 2TB each cap. 12 DDR2 slots @ 8GB each. Loads of fans. It's not quite and draws loads of power. Mine add about $10 to my power bill a month to leave on. I used to do that, but now that I'm collecting degrees and certs (less time free), I only spin them up when I'm using them. 

The specs on the onboards NICs are: Dual embedded Broadcom NetXtreme II&#8482; 5708 Gigabit2  Ethernet NIC with fail-over and load balancing. TOE (TCPIP Offload Engine) support. These cards do say they they are Energy Efficient Ethernet (EEE) ... which their data sheets say the explanation of that is: 
> 
You can help reduce your energy footprint and complement data center energy initiatives through intelligent power management features that meet Energy Efficient Ethernet (EEE) standards.

That has nothing to do with WOL, but an option [COLOR=#444444][FONT=Trebuchet MS]EEE is Low Power Idle (LPI) mode. That mode states in IEEE 802.3az that it optionally allows power saving by switching off part of the integrated Local Area Network (LAN) controller and the 82579 functionality when no data needs to be transmitted and/or received. I know how to do that in Win Server, but have not done that in Linux... (I am running Ubuntu Server 14.04 LTS on all mine.) Honestly, I didn't see that the extra effort of figuring that out to turn off put of a network card was going to amount to much while still pulling power for 2x930W PSU and 10 drives each.[/FONT][/COLOR]

When I dug down deeper into the doc's on my servers:
> 
POWER MANAGEMENT
The adapter speed setting will link at the configured speed for WOL when the system is powered down.
NOTES:
&#8226; For specific systems, see your system documentation for WOL support.
&#8226; WOL is supported in Broadcom NetXtreme II BCM5708 devices with silicon revisions of B2 or later. For more
information, see Limitations.

A quick search of some of my other references on that:
> 
WOL can be enabled in the BCOM NIC Boot Agent. During POST you may see a banner message for the Broadcom NICs. Press Ctrl-S, and it will allow you to enable the WOL option. If you do not see the banner message for the Broadcom NICs at POST, then the banner is disabled. As the system begins POST (wait for the keyboard to initialize), begin pressing ctrl-s repeatedly until the boot agent screen is displayed. From there you can enable the banner and WOL. It may take several tries.


There are not too many reasons to use WOL on a PE2900 server. Better options include purchasing a DRAC 5 and using the DRAC GUI or racadm utility. The racadm utility is included with OM Server Administrator (C:\Program Files\Dell\SysMgt\RAC5). Also the PE2900 includes a BMC on the motherboard and the IPMI protocol can be used to remotely monitor and power the server. The ipmish utility is included with OM Server Administrator (C:\Program Files\Dell\SysMgt\bmc).

So yes, it is possible...

When you set your BIOS boot priority, there's an option in the boot order of what device to boot from, in what order... "Network" is one of those options. As your are booting, in the BIOS extensions from devices as they load, both network card's prompt with a hot-key combo to get into their BIOS settings. WOL is inside their own BIOS settings.

---

### Post by Mike_Ramsey on 2016-01-10
Alas it does indeed have a DRAC gen 5 Controller installed. I am going to try locating the utility for that and see what options are there. Thanks for the additional info.

---

### Post by matt_symes on 2016-01-10
Hi

There you go. Someone else with your server.

MAFoElffen will be able to give you better information about your server than most others on this forum; myself included.

As the server has IPMI, you may find the *ipmitool* package useful.

```
sudo apt-get install ipmitool
```

This may come in useful as well.

Managing Dell PowerEdge Servers Using IPMItool.

[http://www.dell.com/downloads/global/power/ps4q04-20040204-Murphy.pdf](http://www.dell.com/downloads/global/power/ps4q04-20040204-Murphy.pdf)

Kind regards

---

### Post by Mike_Ramsey on 2016-01-10
> **matt_symes said:**
> Hi

There you go. Someone else with your server.

MAFoElffen will be able to give you better information about your server than most others on this forum; myself included.

As the server has IPMI, you may find the *ipmitool* package useful.

```
sudo apt-get install ipmitool
```

This may come in useful as well.

Managing Dell PowerEdge Servers Using IPMItool.

[http://www.dell.com/downloads/global/power/ps4q04-20040204-Murphy.pdf](http://www.dell.com/downloads/global/power/ps4q04-20040204-Murphy.pdf)

Kind regards

Thank you very much Matt this is very useful!

---

### Post by matt_symes on 2016-01-10
Hi

> **Mike_Ramsey said:**
> Thank you very much Matt this is very useful!

It's a useful, if esoteric, tool if you have a board with IPMI.

I've used ipmitool to change the threshold values my fans use to change speed on my Supermicro motherboard.

They kept spinning up and then down, then up, then down, then up........

It was driving me nuts :)

Kind regards

---


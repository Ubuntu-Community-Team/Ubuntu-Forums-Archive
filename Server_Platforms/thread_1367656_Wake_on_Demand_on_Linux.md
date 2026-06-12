---
title: "Wake on Demand on Linux?"
date: 2009-12-29
forum: Server Platforms
---

### Post by ajmas on 2009-12-29
On the MacOS X side Apple implemented something called "Wake on Demand", which allows the computer to sleep and then be woken up by the router when a request is made to that computer:

[http://support.apple.com/kb/HT3774](http://support.apple.com/kb/HT3774)
[http://en.wikipedia.org/wiki/Sleep_Proxy_Service](http://en.wikipedia.org/wiki/Sleep_Proxy_Service)

I am curious to know whether anyone has attempted to replicate this feature in Linux, possibly with Avahi?

---

### Post by kevinatkins on 2009-12-29
I think what you're talking about is 'Wake-On-LAN' which is dependent on hardware support on your particular computer - see here..

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

.. as an aside, and again depending on BIOS support, it's possible to have your computer wake up at a specific time using the on-board real-time clock and suitable software (nvram wakeup) - I used this when I built a Linux PVR, so I could program the thing to wake up to record a TV program, but it was a while ago so I can't remember the exact details...;-)

---

### Post by ajmas on 2009-12-29
> **kevinatkins said:**
> I think what you're talking about is 'Wake-On-LAN' which is dependent on hardware support on your particular computer - see here..

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)


I am definitely talking about "Wake on Demand", which is somewhat higher level to "Wake on LAN". Wake-on-LAN, and Wake-on-Wireless makes use of the MAC address and a magic packet, whereas "Wake on Demand" is higher level and allows waking based on an IP address (from the client computer perspective). 

Basically "WoD" on the host is a Bonjour service that advertises the host as being available to be woken up on demand. The router that is "WoD" aware registers a mapping between the MAC address of the host, how it is connected (to decide whether to use WoL or WoW) and the IP address the host is currently using. Now when a the router receives a request to the host and finds it not responding it will attempt to wake it up. Since this at its most basic level requires WoL and WoW, these must be enabled on the destination host.

I decided to create a ticket at avahi.org for this: [http://www.avahi.org/ticket/296](http://www.avahi.org/ticket/296)

I am aware that only the Apple Airport Extreme implements the router portion at this point, but it would be nice to see this spread to other routers. Maybe this could be included in one of the open source router firmwares, such as DD-WRT?

---

### Post by Vegan on 2009-12-29
I have my server set to snooze unless a request rolls in. The ACPI takes care of everything and I have the CPU throttled back as well as the disks spun down so when its unused it draws little power.

---

### Post by lukeiamyourfather on 2009-12-29
> **ajmas said:**
> Basically "WoD" on the host is a Bonjour service that advertises the host as being available to be woken up on demand.

You already answered your own question. Bonjour is Apple's protocol which is freeware (not open source) for Windows and OS X only. Seems redundant though because you can use WOL or just leave it running which is much less complicated. I'm sure a similar system could be created but it wouldn't be using Bonjour nor would it be compatible with it. Cheers!

---

### Post by Dr. Kenneth Noisewater on 2010-04-30
> **lukeiamyourfather said:**
> You already answered your own question. Bonjour is Apple's protocol which is freeware (not open source) for Windows and OS X only.

Incorrect.  Bonjour is an implementation of the open Zeroconf protocol.

---

### Post by ajmas on 2010-05-06
> **lukeiamyourfather said:**
> You already answered your own question. Bonjour is Apple's protocol which is freeware (not open source) for Windows and OS X only. Seems redundant though because you can use WOL or just leave it running which is much less complicated. I'm sure a similar system could be created but it wouldn't be using Bonjour nor would it be compatible with it. Cheers!

Bonjour is the trademark that Apple's implementation of mDNS:

[http://en.wikipedia.org/wiki/Zero_configuration_networking](http://en.wikipedia.org/wiki/Zero_configuration_networking)

Anyone is free to provide an implementation for their platform. In fact numerous printers incorporate mDNS for discovery on the local network.

---

### Post by m00dawg on 2011-01-15
The issue is not Bonjour though, it's about setting up the BIOS to wake if the NIC detects that a packet was sent to the server. Basically, turn everything off except the NIC and set some sort of interrupt.

I agree that WoL and WoD are two different beasts here. If my fileserver is sleeping at the time I want to might my file-share on my laptop, for instance, that request should cause it to wake up. As opposed to having to send a magic packet. I can do that no problem, my wife can't :) Nor can my remote servers that access my file-server send those types of packets (I don't think) because they only work locally.

I have tried experimenting around with BIOS settings, but not to a great deal to get this to work. I do have a script that might be mildly helpful for making the machine go to sleep however:

```

#!/bin/bash
hdparm -C /dev/sda | grep "active" > /dev/null
SDA=$?
hdparm -C /dev/sdb | grep "active" > /dev/null
SDB=$?
if [ $SDA -eq 1 ] && [ $SDB -eq $SDA ]
then
	echo "drives asleep"	
	LOAD=`awk {'print $1'} /proc/loadavg`
	echo $LOAD
	if [ "$LOAD" == '0.00' ]
	then
		echo "load hit threshold"
		echo "Sleeping"
		# Call sleep process here
	fi
fi

```

There are a few ways to make the machine sleep, so I left that part blank because I haven't decided on which one to use :) But the logic seems sound. This is for a NAS, so I only want to sleep if there is no load AND the drives are already asleep.

Hope that helps!

---

### Post by m00dawg on 2011-01-15
Doh self post fail :) I was reading the [Wikipedia]("http://en.wikipedia.org/wiki/Wake_on_LAN#Other_machine_states_and_LAN_wakeup_signals") page on WoL and found this tidbit:

> 
The machine's BIOS must be set to allow Wake-on-LAN. To allow wakeup from powered-down state S5, wakeup on PME (Power Management Event) is also required. The Intel adapter allows "Wake on Directed Packet", "Wake on Magic Packet", "Wake on Magic Packet from power off state", and "Wake on Link".[17] Wake on Directed Packet is particularly useful as the machine will automatically come out of standby or hibernation when it is referenced, without the user or application needing to explicitly send a magic packet. Unfortunately in many networks waking on directed packet (any packet with the adapter's MAC address or IP address) or on link is likely to cause wakeup immediately after going to a low-power state. Details for any particular motherboard and network adapter are to be found in the relevant manuals; there is no general method. Knowledge of signals on the network may also be needed to prevent spurious wakening.


So this implies, to me, that various options are possible here. But I think it's far more dependent on the hardware than it is Linux. The only thing Linux can hope to do is, I think, tell the BIOS to enable WoL and other such things. The actual work being done is all low-level between the BIOS and NIC it would seem.

Hope that helps! Again sorry for the self reply.

---

### Post by ajmas on 2011-01-15
From what I remember reading a few things need to be in place before 'wake on demand' works:
  - Router that is WoD aware
  - Computer is able to be woken by a magic packet
  - Computer advertising a given service via mDNS, say SSH
  - Computer advertising it is accepting to be WoD, via mDNS

WoD uses a WoL at the lower level, but will only wake a PC on demand if it there is a service that is being advertised. I have been having issues simply doing a WoL with my Linux PC, so I can't even establish whether what I read is correct. Maybe this if someone can try this out, it would confirm whether the information is accurate.

---

### Post by ajmas on 2011-01-15
From what I remember reading a few things need to be in place before 'wake on demand' works:
  - Router that is WoD aware
  - Computer is able to be woken by a magic packet
  - Computer advertising a given service via mDNS, say SSH
  - Computer advertising it is accepting to be WoD, via mDNS

WoD uses a WoL at the lower level, but will only wake a PC on demand if it there is a service that is being advertised. I have been having issues simply doing a WoL with my Linux PC, so I can't even establish whether what I read is correct. Maybe this if someone can try this out, it be able to confirm whether the information is accurate.

---

### Post by ajmas on 2011-01-15
From what I remember reading a few things need to be in place before 'wake on demand' works:
  - Router that is WoD aware
  - Computer is able to be woken by a magic packet
  - Computer advertising a given service via mDNS, say SSH
  - Computer advertising it is accepting to be WoD, via mDNS

WoD uses a WoL at the lower level, but will only wake a PC on demand if it there is a service that is being advertised. I have been having issues simply doing a WoL with my Linux PC, so I can't even establish whether what I read is correct. Maybe this if someone can try this out, it be able to confirm whether the information is accurate.

---

### Post by ajmas on 2011-01-15
From what I remember reading a few things need to be in place before 'wake on demand' works:
  - Router that is WoD aware
  - Computer is able to be woken by a magic packet
  - Computer advertising a given service via mDNS, say SSH
  - Computer advertising it is accepting to be WoD, via mDNS

WoD uses a WoL at the lower level, but will only wake a PC on demand if it there is a service that is being advertised. I have been having issues simply doing a WoL with my Linux PC, so I can't even establish whether what I read is correct. Maybe this if someone can try this out, it be able to confirm whether the information is accurate.

---

### Post by ajmas on 2011-01-15
From what I remember reading a few things need to be in place before 'wake on demand' works:
  - Router that is WoD aware
  - Computer is able to be woken by a magic packet
  - Computer advertising a given service via mDNS, say SSH
  - Computer advertising it is accepting to be WoD, via mDNS

WoD uses a WoL at the lower level, but will only wake a PC on demand if it there is a service that is being advertised. I have been having issues simply doing a WoL with my Linux PC, so I can't even establish whether what I read is correct. Maybe this if someone can try this out, it be able to confirm whether the information is accurate.

---

### Post by m00dawg on 2011-01-15
I was able to get this working (sotra) by adding these lines to my /etc/rc.local:

```

/sbin/ethtool -s eth0 wol "pug"
echo enabled > /sys/class/net/eth0/device/power/wakeup

```

The first command configures the WoL properties - namely physical, unicast, and MagicPacket. The second actually enables the NIC to wake-up on events. It was not working before-hand so after Googling around I noticed that some OS'es do not set this for you (nor does 'ethtool', though I think it should).

After doing that, I was able to wake my machine up simply by trying to SSH in to the machine.

My problem now is that it doesn't like to suspend to memory - it comes back to life once doing so, but the OS does not respond and I have to power off the machine to get things right. Going into standby doesn't turn off the PSU fan though but I guess it's better than nothing.

To initiate various sleep states, I have been using ACPI:

```

# cat /sys/power/state 
# echo "standby" > /sys/power/state

```

So, while your mileage may vary, I did NOT need mDNS for any of this to work. I just needed to configure my NIC appropriately.

---

### Post by ajmas on 2011-01-16
Turns out my Linux PC may be having more hardware issues than expected, so it it is limiting my testing. Could someone with an Ubuntu 10.10 based system, using an Apple Airport Extreme base station try the following:

- ensure your computer can be woken using WoL
- install the ssh server (if it is not installed)
- make the ssh service available via mDNS: 
  
```
sudo cp /usr/share/doc/avahi-daemon/examples/ssh.service /etc/avahi/services
```

- create the file /etc/avahi/services/wakeondemand.services and provide the following content:

```
<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_sleep-proxy._udp</type>
    <port>56018</port>
  </service>

</service-group>

```
- check with another computer to see whether both services are being advertised
- put the first computer to sleep
- from the second computer try doing an ssh <computername>.local and see if the first computer wakes up.

---

### Post by generator85 on 2012-01-17
Did you guys ever manage to get this fully working? If yes: how? I've tried the mentioned methods, but it doesn't seem to be working.

---

### Post by rubylaser on 2012-01-17
1. You need to enable wake via PCI device in your BIOS.
2. You need to install ethtool
```
sudo apt-install ethtool
```
3. Verify you NIC supports WOL.
```
fileserver:~# ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	**Supports Wake-on: g**
        Wake-on: n
	Link detected: yes
```
4. If it does, enable it.
```
sudo ethtool -s eth0 wol g
```
5. If you want it to survive a reboot add it to your network interface init script like this.
```
sudo nano /etc/network/interfaces
```
and add a line like this in your device settings.```
iface eth0 inet dhcp 
up ethtool -s eth0 wol g
```

---

### Post by Bolsoe on 2012-01-21
> **rubylaser said:**
> 
1. You need to enable wake via PCI device in your BIOS.
..
2. You need to install ethtool
..
3. Verify you NIC supports WOL.
..
4. If it does, enable it.
..
5. If you want it to survive a reboot add it to your network interface init script like this.
..


This will only enable wake-on-lan using a magic packet, not wake-on-demand (where the server wakes up when a service port is accessed, for instance samba or ssh). Even wake-on-lan can be quite tricky, if you have a realtek ethernet card, for instance, the default r8169 driver seems like it provides wake-on-lan, but it does not work. Use the r8168 driver instead ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160413](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/160413))

Proper wake-on-demand is usually implemented by having a wod-capable router that can act as a proxy for the server, and send a magic packet if a service port is accessed. See the earlier posts for more information. This is for instance how Apple implements their Wake-on-Demand service. I believe there are simple script-based implementations available for open-sourced routers (like dd-wrt or openwrt) that can do partly do the same thing. A lot of tinkering is required, though.

I chose a different approach. I bought a wake-on-unicast-capable ethernet card (Intel GT Pro 1000, $10 on ebay) and installed that. Instead of the "g" (magic packet) option it is then possible to use "ethtool -s eth0 wol u" (wake on any packet sent directly to the network card). This works fine: The server goes to sleep, but if you try to connect directly to it (samba, ssh, http or anything else) it will wake up. However, after a few minutes the arp cache of the client computer will be cleared, and since the server is asleep and does not respond to arp requests, the client does not know which mac-address to talk to anymore. No more waking up :-(
I took an old linksys 54g router i had around, installed openwrt on it, and modified the arpd daemon to be able to respond to arp-requests for the sleeping server. The linksys router uses like 3 watts of power, so it is OK to leave it on 24/7. This setup seems to work brilliantly, and has been running for the past six months with no hiccups. This approach however, also requires a lot of tinkering, and a bit of programming. WOD for linux is definitely not ready for the masses yet :-)

---

### Post by kevinthecomputerguy on 2012-01-22
+1 Rubylaser

Non of this works without ethtool -s

I use it in /etc/rc.local to fit my needs (assuming bios is also setup right)

Wake from sleep is an entire different approach, that's why your getting so many different views. Wake on Lan is king in my opinion.

---

### Post by macoxp on 2012-05-23
> **ajmas said:**
> Turns out my Linux PC may be having more hardware issues than expected, so it it is limiting my testing. Could someone with an Ubuntu 10.10 based system, using an Apple Airport Extreme base station try the following:

- ensure your computer can be woken using WoL
- install the ssh server (if it is not installed)
- make the ssh service available via mDNS: 
  
```
sudo cp /usr/share/doc/avahi-daemon/examples/ssh.service /etc/avahi/services
```

- create the file /etc/avahi/services/wakeondemand.services and provide the following content:

```
<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_sleep-proxy._udp</type>
    <port>56018</port>
  </service>

</service-group>

```
- check with another computer to see whether both services are being advertised
- put the first computer to sleep
- from the second computer try doing an ssh <computername>.local and see if the first computer wakes up.

I tried this on my system that works with magic packet. as soon as i put the computer to sleep the computer's bonjor broadcast drops off the network it is never passed to my airport extreme.

---

### Post by waini on 2012-06-08
This can't be done by using avahi because it requires sending a special DNS-Request to the SleepProxyServer.

But there is a new project on github to get this working: [https://github.com/awein/SleepProxyClient](https://github.com/awein/SleepProxyClient)

---


---
title: "Hibernate server when not in use over network"
date: 2014-10-06
forum: Server Platforms
---

### Post by D.Dadsgé on 2014-10-06
Hi everyone

I've recently set up a new media/streaming server using minidlna, which is working fine. But as I am trying to perfect the system, I bumped into some problems.


[LIST]
[*]My first problem is on the power management part: as I will keep the server available 24/7, I'd like it to go to a hibernate state when nobody on the network is using the server. This way I can keep the power usage to a minimum (and keep the noise down, damn those fans...). I noticed ubuntu doesn't automatically check for network usage when auto-suspending/hibernating. For example: I was transferring files from my laptop to the server using Samba and after a while the connection dropped (auto sleep/suspend I guess). I have looked around on the internet and I wasn't able to find the exact thing I'm looking for.
[/LIST]
[INDENT]My solution:[/INDENT]
[INDENT]I already disabled the auto-sleep/suspend and now I would like to create a script which will be run by cron every 15 mins or so. The script should check if the network is in use, if so, it should just remain operational until it checks again, if not, it should hibernate the system. The problem here is that I don't know very much about scripting or how it would check for network usage.[/INDENT]


[LIST]
[*]For the second problem I retake my example from before: So as I said, ubuntu will still go in sleep/suspend mode when Idle (not looking at the network part now), but let's call it the X-state as I am not entirely sure it is a sleep/suspended state. I have the server right next to me, and for as far as I can tell, there is no notable difference between the working state and the X-state. The fans are still running at the same speed and the lights don't go off as they would do if I manually hibernate it. The problem here is that the server becomes virtually unreachable. SSH/samba/apache/ping all seem to fail, I've tried waking it with WoL but that doesn't work either. Even the power button doesn't bring it back any more. I can only reboot the whole system by forcing the server to shut down using the power button. Is there something I'm missing here? Is this X-state as I guessed indeed a Sleep/Suspended state and do I just not know how to bring it back? For the moment I disabled the auto-sleep/suspend as I told before, but I'd like to know what's going on here.
[/LIST]


[LIST]
[*]My last problem (so far) is that I cannot wake the server using XBMC.
[/LIST]
[INDENT]I am using XBMC as a mediareceiver to connect to the streaming server. Since I am now manually hibernating my system, I would like it to wake up when using XBMC. I read about the "Advanced Wake On Lan" add-on, I installed it, but it does not seem to work for me. Although when I use a program like wakeonlanx, I am able to use the WoL function and boot up the system again. I have tried to enter my mac address of my server in different ways (using ":", "-" or "" as a separator, using capital or lower-case letters) but none seem to work.[/INDENT]
[INDENT]I didn't really find a solution here yet since I cannot locate where the problem is...[/INDENT]

Phew, so far that's all of it. I hope you guys can help me out with these problems, or point me in the right direction so I can solve it myself :)

Kind regards
D.Dadsgé

---

### Post by tgalati4 on 2014-10-06
Is Wake-on-LAN (WoL) turned on?

Open a terminal:

```
ethtool -a eth0
```

Your network card can be found with:

```
ifconfig
```

Some network cards need the -g switch turned on with each boot--the setting is not sticky on some cards.  Put it in a boot script like /etc/rc.local above the *exit 0* stanza.

---

### Post by cariboo on 2014-10-07
I have an auxiliary minidlna server where I use WOL to start it up, you have to use a couple of extra commands to start it up and shut it down, but I find it much faster to boot, than coming out of suspend or hibernate.

---

### Post by D.Dadsgé on 2014-10-07
I used [this site ]("https://help.ubuntu.com/community/WakeOnLan")to set up my WoL and it works perfectly when i hibernate my machine. I also added the script part to /etc/network/interfaces, so WoL is enabled at boot. I am currently not home, so i cannot issue any commands to my server...

---

### Post by D.Dadsgé on 2014-10-09
Ok, I'm at my apartment now. I tried the ethtool command, it returns me this error: "Pause parameters for eth0: Cannot get device pause settings: Operation not supported"

When I use the pm-hibernate or pm-suspend command manually, I am able to wake the server up with [wakeonlanx]("http://wakeonlanx.com/wakeonlanx/"). So I guess it's not a problem with the WoL being disabled..?

---

### Post by tgalati4 on 2014-10-09
What card are you using?

> 
gates@GNAS ~ $ ethtool -i eth0
driver: tg3
version: 3.134
firmware-version: 5751-v3.44a
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no


If WoL works between boots, then you should be OK.  If it only works once, then you need to put in the boot script.  Some cards lose the setting when power is lost.  Not a problem usually with a server and an UPS to provide power.

> 

gates@GNAS ~ $ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off
**	Supports Wake-on: g**
**	Wake-on: g**
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes


Now that WoL is working, put a launcher on every computer, tablet, phone.

Then set the go-to-sleep parameters of your media server to 1 hour.  If there is no activity in 1 hour--your system will go to sleep.

For linux systems, there are several tools:

```
apt-cache search wake
```

I think a reliable WoL setup will take care of points 1, 2, and 3.

---

### Post by D.Dadsgé on 2014-10-09
I just rebooted the system to make sure the WoL actually works between boots, but now the pm-hibernate and pm-suspend commands don't work any more...  When I use the suspend command in putty, it doesn't do anything, it just goes to the next line. The hibernate command does kind of feel like it's going to sleep, all network connections are lost, but the system keeps on running... Same here as I said in number 2. Not even WoL gets the network connection running again, only a full reboot does the trick :/

I am running an Ubuntu 12.04 server, just so you know. I read some commands have been updated after 12.04.

Here are the outputs of the ethtool:

ethtool -i eth0:
> driver: ATL1Eversion: 1.0.0.7-NAPI
firmware-version: L1e
bus-info: 0000:01:00.0
supports-statistics: no
supports-test: no
supports-eeprom-access: no
supports-register-dump: yes

sudo ethtool eth0:
> Settings for eth0:    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    [B]Supports Wake-on: pg
    Wake-on: g[/B]
    Current message level: 0x00000000 (0)
                   
    Link detected: yes

---

### Post by tgalati4 on 2014-10-09
The "p" mode is pause mode, which may or may not work.  You need to turn that mode off.  You want the connection to go down and go up during each sleep-wake cycle.  "Pause" causes an indeterminate network state--especially for a media server.  

Only use hibernate when your swap size is bigger than your RAM, otherwise you will get bad behavior.

```
free
```

---

### Post by D.Dadsgé on 2014-10-10
I don't think the "p" option is set on my network card, as it only says it is supported. 
> Supports Wake-on: pg
Wake-on: g
and the Wake-on option is only set to g, so no problems there.

I also checked if my swap is indeed big enough for the ram to be copied to.>              total       used       free     shared    buffers     cachedMem:       2049116     724916    1324200          0      37076     435204
-/+ buffers/cache:     252636    1796480
Swap:      4901884          0    4901884

2 gigs of RAM and 5 gigs for swap, apparently I kinda overdid it there, but that seems to be OK as well.

I still can't find the problem with pm-hibernate and pm-suspend...

---

### Post by D.Dadsgé on 2014-10-13
Ok, I got desperate and installed ubuntu 14.04 from scratch (was in 12.04) and it all seems to work fine now. Got my minidlna set up, xbmc can now also wake my server and pm-hibernate works like it should work.
Thanks everyone for trying to help me out!

---


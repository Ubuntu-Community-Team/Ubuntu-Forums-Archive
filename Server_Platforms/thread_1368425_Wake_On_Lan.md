---
title: "Wake On Lan"
date: 2009-12-30
forum: Server Platforms
---

### Post by humphreybc on 2009-12-30
I'm trying to get wake on lan working for my home file server.

I've set it up in the BIOS so that WOL should be enabled, and I'm sending this as the magic packet using wakeonlan:

```

wakeonlan -i 192.168.1.2 -p 22 00:00:00:00:00:00

```

Where the zeros are my Mac address. But it doesn't want to wake up.

That's my correct IP address for the server and I also tried 192.168.1.1 for the router, and the port number is what ssh uses so I thought that it should work...

Also, the LAN1 light on the router is still lit up when the computer is powered down, so that means the system is still giving 5V to the network card to listen for the magic packet.

Does it have to be port 9? Perhaps it's something to do with my router blocking that port. I've looked into port forwarding but can't seem to find any options in the router admin.

---

### Post by Muttley99 on 2009-12-30
Try using the mac address for the machine you want to wake only - mine works fine that way.

---

### Post by humphreybc on 2009-12-30
So you mean like:

```

wakeonlan 00:00:00:00:00:00

```

I tried that but still no luck. :S

---

### Post by Muttley99 on 2009-12-30
> **humphreybc said:**
> So you mean like:

```

wakeonlan 00:00:00:00:00:00

```

I tried that but still no luck. :S

Check wakeonlan is installed!

try port 7 (you tried 9?)

[HTML]wakeonlan -p 7 00:00...........[/HTML]

---

### Post by volkswagner on 2009-12-30
Can you watch the NIC light while you send the wake command?  If you can see blink activity you can eliminate the router, which most likely is not the cause if you are initiating inside your lan.

What type of PC or network card is installed.  I have found several makes such as Dell and HP only allow WOL when in standby and not in full off state, even though the NIC stayed lit while off.

Have you checked the following thread?

[http://ubuntuforums.org/showthread.php?t=360901](http://ubuntuforums.org/showthread.php?t=360901)

---

### Post by Vegan on 2009-12-30
ACPI makes this unnecessary as the machine in a snooze will come to life.

Really old machines may need a tentacle, but built-in NICs support is connected permanently.

My server snoozes and comes alive fine. I did change the power option to be more aggressive to save on power.

---

### Post by humphreybc on 2009-12-30
Yep I watched the LAN1 light on the router and it blinks three times when I send it to 192.168.1.2 on port 7.

Also the orange light at the back of the computer beside the ethernet plug blinks when I send it as well.

The NIC is integrated into the motherboard.

It's a fairly new computer, the BIOS has a tonne of options that are good for servers so I'm sure it can start from power off.

Also, I've set it so when the front button is held down it goes into soft off - but I'm not sure what happens when I issue sudo shutdown -h now from openssh remotely. It may not go into "soft sleep" then...

Here's my ethtool output on eth0:

```

	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

---

### Post by humphreybc on 2009-12-30
Oh far out I fixed it. All I had to do was enable wake on lan using ethtool in that thread, and then add it to the startup options!

Yay it works!

---

### Post by Muttley99 on 2009-12-30
Nice one! Have you tried powernap yet?

---


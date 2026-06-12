---
title: "Alternative to DRAC card?"
date: 2015-03-09
forum: Server Platforms
---

### Post by Vincent_Orange on 2015-03-09
I have 5 servers for home use, and other various non-continuous use. I have a rack in my loft and so I can access the machine with a ladder. Is there a solution to monitoring the machine and turning it on/off as needed with out using a DRAC Card... like this [https://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us](https://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us)

Any suggestions?

---

### Post by sandyd on 2015-03-09
> **Vincent_Orange said:**
> I have 5 servers for home use, and other various non-continuous use. I have a rack in my loft and so I can access the machine with a ladder. Is there a solution to monitoring the machine and turning it on/off as needed with out using a DRAC Card... like this [https://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us](https://www.dell.com/content/topics/global.aspx/power/en/ps2q02_bell?c=us)

Any suggestions?

See if KVM-Over-IP switch is affordable, if not

Another solution is to setup WoL to force computers to wake up and just use SSH to access. If you use a software router like pfsense, you can just boot the server from pfsense.

Monitoring can be done using monitoring programs (i.e. icinga2/nagios/zabbix/etc)

Side note: The main purpose of DRAC is to provide out-of-band management, which would still work if the server had been stuck at grub, crashed, or had issues preventing it from booting. If you need these features, either KVM-Over-IP or DRAC is the way to go.

---

### Post by tgalati4 on 2015-03-10
DRAC is overkill if the servers are physically reachable.  Besides WoL (which is probably best suggestion), you could use a 4-way KVM switch and then run a long VGA and USB cable to your monitor location, like a shelf behind the ladder.  DRAC cards allow access to the error logs that are actually stored in the BIOS nvRAM, which is neat, but really only useful if the servers are in a remote location.

With WoL, you can use a WoL app on your phone to wake your servers and an ssh client on the phone to put them to sleep.

---

### Post by lukeiamyourfather on 2015-03-10
There are lots of alternatives but each manufacturer has their own solution. The servers I typically work with are Supermicro and they have their own IPMI solution. If you have a bunch of random servers you could do something like a Raspberry Pi (or Raspberry Pi 2) and use the GPIO pins to monitor if a machine is powered on and to trigger the power switch on a machine remotely.

---

### Post by Vincent_Orange on 2015-03-11
Lots of good suggestions here. I'll try the WoL method as it seems a good software solution for my requirements.

---

### Post by tgalati4 on 2015-03-12
Be mindful that some Dell servers (like the PowerEdge 1750) won't remember the WoL settings and have to be set in a script in /etc/rc.local.  Settings get lost because network card doesn't store them--who would put a server to sleep?  Not a Use Case that a server was designed for.  You may also have to keep power to the network card using *acpitool*.  Again, another Use Case that was not considered for a server.

---


---
title: "What do you make of these kernel messages"
date: 2008-02-01
forum: Server Platforms
---

### Post by Sporkman on 2008-02-01
I'm running a remote dedicated webserver on Ubuntu 7.10 server, and in the middle of the day today the site went down. The server also didn't respond to pings or ssh, so I had to contact the hosting co & use up a reboot...

So I'm looking through the logs to see if I could figure out what went wrong, and this is the only out-of-the-ordinary thing:

```
Feb  1 10:57:57 sp4010c -- MARK --
Feb  1 11:17:57 sp4010c -- MARK --
Feb  1 11:30:21 sp4010c kernel: [903734.866027] eth1: link down
Feb  1 11:30:23 sp4010c kernel: [903737.183907] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Feb  1 11:30:59 sp4010c kernel: [903772.298194] eth1: link down
Feb  1 11:31:04 sp4010c kernel: [903778.215267] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Feb  1 11:31:07 sp4010c kernel: [903780.656016] eth1: link down
Feb  1 11:31:09 sp4010c kernel: [903782.973892] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
Feb  1 11:48:50 sp4010c syslogd 1.4.1#21ubuntu3: restart.

```

Anybody know what that's about?

---

### Post by ssuehr on 2008-02-01
Are you referring to just the eth1 messages?

It seems like a cable was unplugged or whatever eth1 was connected to got power cycled.  Those would be my initial guesses.  Otherwise I suppose someone could've been restarting networking too.  Any other symptoms or issues?

Steve

---

### Post by Sporkman on 2008-02-01
> **ssuehr said:**
> Are you referring to just the eth1 messages?


Yes, those are the only system messages occuring before the outage.

> **ssuehr said:**
> It seems like a cable was unplugged or whatever eth1 was connected to got power cycled.  Those would be my initial guesses.  Otherwise I suppose someone could've been restarting networking too.  Any other symptoms or issues?


Hmm, maybe the whole thing was the hosting co's fault, maybe they were mucking around with their network. No other issue, just the unexpected & unwelcome outage (which was solved by a reboot).

---


---
title: "Remote Server Startup"
date: 2010-01-01
forum: Server Platforms
---

### Post by Bushflyer on 2010-01-01
I will be running a desktop with Ubuntu Server Edition on it.  This computer, when it is deployed, will be in a location that is subject to heavy thunderstorms in certain parts of the year and is a quite long drive from both my organization's place of business and my residence.  Although there is already a UPS available to shut it down in case of an outage, the organization I am handling this project for does not have the budget to purchase a US$275 phone-controlled power switch with which to start it back up after said power outage.  I am wondering if Ubuntu Server Edition has a software- or BIOS-side capability to remotely start up from **non-LAN** computers.

---

### Post by volkswagner on 2010-01-01
Wake on Ring is the only thing that comes to mind.  If it is supported by the MOBO (BIOS) and modem may help.

Since the unit is attached to a UPS, I don't think the auto power on setting in the bios will help since the UPS probably sends a gracefull shutdown command, and the ups nerver shuts power off at the power socket.

You may be able to set a scheduled power on in the BIOS for every morning.  If the unit is already on, this should not affect anything as far as I know.  But it may save a trip.

---

### Post by noway2 on 2010-01-03
The last and admittedly inexpensive PC I bought had a BIOS option to automatically restart when power has been restored.  Perhaps your server has something similar?

---

### Post by Bushflyer on 2010-01-03
The computer in question is currently inaccessible (at least six hours away) so I would not know if it had that option in the BIOS.  I was simply wondering if Ubuntu Server Edition had that feature.

---

### Post by HermanAB on 2010-01-04
Cheap UPS devices will cause a shutdown almost immediately on power failure.  So, maybe you should use a more capable UPS and set the shutdown timeout to a longer limit so the server can stay up long enough to ride out the storms?

---

### Post by CharlesA on 2010-01-04
> **HermanAB said:**
> Cheap UPS devices will cause a shutdown almost immediately on power failure.  So, maybe you should use a more capable UPS and set the shutdown timeout to a longer limit so the server can stay up long enough to ride out the storms?

I've got APC UPS(es?) hooked up to my machines at home. I've used apcupsd to set it up to do graceful shutdowns in the event of a power outage. The one I've got can run the server for approximately 10 minutes (APC Back-UPS ES 450 at about 50% load).

I don't know if it would be worth it to get a larger UPS that can run the machine on battery power long enuff to ride out the storm. It would depend on how often the power goes out, and for how long.

In the bios, should be an option for "last state" or "always on" in the event of power loss.

---


---
title: "how do I un&quot;stealth&quot; my ports?"
date: 2008-07-18
forum: Security
---

### Post by daisuke666 on 2008-07-18
I woke up this morning and it seems my bit torrent programs can no longer connect to trackers. 
I tested my ports on multiple sites and it seems the port/s for torrent have been "stealthed", how can I open these?

My other PC with xp installed can connect to trackers through that port fine.

---

### Post by Vorian Grey on 2008-07-18
Sounds like you have ufw (uncomplicated firewall) enable. To configure it to allow your bit torrent to work, see here...

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

Or do you us another firewall?

---

### Post by Vivaldi Gloria on 2008-07-19
> **daisuke666 said:**
> I woke up this morning and it seems my bit torrent programs can no longer connect to trackers. 

If they were able to connect in the past but not now then you must have changed something. Don't you know what you changed?

---

### Post by The Cog on 2008-07-19
If your ports are really stealthed, you will be able to see so by looking at your iptables rules. First off, use this command to see if your firewall is active:
**sudo iptables -nvL**
It will give you three headings. If there are any rules under the headings, you will have to figure out what's putting them there. If there are no rules, then your ports are not stealthed and you will need to start looking for another reason things aren't working.

---


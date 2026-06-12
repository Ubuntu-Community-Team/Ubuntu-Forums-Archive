---
title: "Ubuntu or other Linux distros vulnerable to VPNFilter?"
date: 2018-06-12
forum: Security
---

### Post by kpatz on 2018-06-12
I've been reading about the VPNFilter malware which has been infecting routers and other network devices worldwide.

Since many consumer routers' firmware are Linux based, is it possible that Ubuntu or other Linux distros running on a PC could also be vulnerable?  I haven't been able to find anything on this.

On my home network I run an Atom based mini ITX box running Ubuntu Server 14.04 (I need to upgrade this soon) using iptables as a firewall/router.  The only service running that's open to the WAN side is ssh on a high-numbered port, with no password access, only keys.

I don't think this is vulnerable to these consumer router type malware, but I want to be sure.  I do keep it up to date.

---

### Post by TheFu on 2018-06-12
> Most of the devices targeted are known to use default credentials and/or have known exploits, particularly for older versions. There is no indication at present that the exploit of zero-day vulnerabilities is involved in spreading the threat.
from [https://www.symantec.com/blogs/threat-intelligence/vpnfilter-iot-malware](https://www.symantec.com/blogs/threat-intelligence/vpnfilter-iot-malware)

Sounds like you are doing everything right. Do you run denyhosts or fail2ban to protect ssh a little more?   Do you have daily, versioned, backups?  With those, comparing file diffs should any issue happen wouldn't be hard.

I have a few 14.04 systems left.  Plenty of time to upgrade, 9 months.

IMHO, using a properly maintained, minimal, Linux server or BSD server OS for routing is the smartest thing today. Trusting most soho/consumer routers to be maintained has proven to be unwarranted trust though the MikroTik and ubiquiti guys have a good history of very quick patch support.

---

### Post by kpatz on 2018-06-18
Thanks... I do use fail2ban.  I deliberately picked a port that I've never seen scanned in my logs for my ssh... though now I almost never use it from outside so I may close it off from the WAN side anyway... maybe when I upgrade to 18.04 in the coming months.  I also have iptables rules set up so only a couple connections per IP per 10 minutes is allowed.

I do weekly backups to my zfs file server, so diffs are possible.

---

### Post by TheFu on 2018-06-18
I think you are pretty well covered, probably more secure than me, and most people here would call me paranoid.
At a linux conference last weekend, in a gpg session, the presenter suggested using Elliptic curve ed25515 ssh certs (or keys) for better encrypted ssh connections.  Since 14.04, many of the ssh ciphers have been determined to be less secure than previously believed and default key sizes are much longer.

I wouldn't worry too much about remote ssh attacks when you have it setup like you do.  Daily, I have a script that checks my systems for failed ssh attempts.  On port 22/tcp, there were thousands per hour from thousands of different source addresses.  Moving to any other unpopular port stopped that completely.  I haven't seen anything in the system logs or the router logs since making that change about 10 yrs ago.

---


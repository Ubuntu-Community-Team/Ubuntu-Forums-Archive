---
title: "Detecting compromised systems on LAN"
date: 2008-03-31
forum: Security Discussions
---

### Post by FakeOutdoorsman on 2008-03-31
There are several Windows machines on my LAN.  I want to passively monitor the Windows computers to detect if they are probing around to infect other LAN users.  I've been using farpd and honeyd honeypots on my Ubuntu machine to see what machines might be probing unused local ip addresses.  It seems to work, but I would like to do more.  Any suggestions for what else I could be doing to detect any rogue machines?

---

### Post by sbenson on 2008-04-07
For a simple try:

I'd use ethereal or wireshark.


For more complex:

Log all your firewall outbound to a ossec type SIM server, maybe put agents on the boxen.
And throw a honey pot on the subnet with all the win32 boxes, make sure it's showing samba services and log iptables on it, send it all to the SIM/syslog server.

and the best:

upgrade to linux on all systems: problem solved :)

---

### Post by jba6511 on 2008-04-08
network intrusion detection system. Look at setting up snort.

---

### Post by lwr07 on 2008-04-08
I'd have to say Snort also.  Here's a really good guide for setting it up on Debian based systems.

[http://www.snort.org/docs/setup_guides/deb-snort-howto.pdf]("http://www.snort.org/docs/setup_guides/deb-snort-howto.pdf")

BASE will give you a decent front-end for Snort but I've had a lot of problems with it becoming really slow once it hits a million records.  If you decide to use it and have similar issues let me know and I'll post a script that moves your data to an archive db after it becomes x number of days old.

---

### Post by FakeOutdoorsman on 2008-04-08
> **sbenson said:**
> For a simple try:

I'd use ethereal or wireshark.


For more complex:

Log all your firewall outbound to a ossec type SIM server, maybe put agents on the boxen.
And throw a honey pot on the subnet with all the win32 boxes, make sure it's showing samba services and log iptables on it, send it all to the SIM/syslog server.
...

Thanks for the suggestions.  I use Wireshark and it is a nice tool, but these are coworker machines and I don't want to pester anyone with software installation.

It's been quiet so far on the honeyd front, but it's only been active for a few days.

---

### Post by FakeOutdoorsman on 2008-04-09
Here's an interesting one: [Using Nepenthes Honeypots to Detect Common Malware]("http://www.securityfocus.com/infocus/1880").

---


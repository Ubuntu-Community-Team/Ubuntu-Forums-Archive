---
title: "VMWare Security"
date: 2006-04-18
forum: Server Platforms
---

### Post by markr on 2006-04-18
I have ClamAV and Firestarter (IPTables) installed and running.  I have also just installed WinXP under VMWare so I can get access to soem work stuff.

My VMWare installation is using NAT to connect to the web; do I need to install zoneAlarm and AVG in my Windows guest, or will my current Linux security measures handle any viruses/attacked (because I am using the same IP address as my Linux Host, I had assumed that IPTables would handle any attacks)?

Sorry if the answer is obvious, but I'm just getting up to speed on Linux security/network issues.

---

### Post by jclw on 2006-04-18
Everything going to WinXP passes through your Linux box and thus through iptables. So the system running in VMWare will be secured by you Linux firewall. However, your firewall can't protect you from viruses spreading via eMail and the like. As I don't think you are processing mail inside VMWare, you should be pretty safe whithout any extra anti-virus software. [But be careful with windows viruses that could be hidden in your shared folders on the Linux host]

---


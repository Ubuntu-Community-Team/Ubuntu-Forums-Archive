---
title: "Port 21 reported open by nmap and netcat, but blocked by iptables"
date: 2010-10-11
forum: Server Platforms
---

### Post by NIT006.5 on 2010-10-11
Strange issue here when trying to verify firewall on Server 8.04. No ftp service running at all on server, but both nmap and netcat report port 21 as being open, even though it isn't. 

I am 100% sure that port 21 is not actually accessible and iptables rules are fine. Trying to connect to the port fails, yet nmap and netcat seem to report a "false positive"?

Got me stumped. Any ideas?

Have also checked on a number of other servers I'm running, and this "false positive" seems to apply to all of them.

---

### Post by NIT006.5 on 2010-10-11
My bad! Problem was with a device on my route to the Internet and had nothing to do with the servers.:oops:

---


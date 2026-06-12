---
title: "Odd server behavior (in DMZ)"
date: 2008-11-19
forum: Server Platforms
---

### Post by dgersting on 2008-11-19
I have an Ubuntu Server (8.04) which is in my router's demilitarized zone. This server currently has SSH, Apache, and Bind9 installed as it will soon become a proxy and local nameserver for my LAN.

**From within my LAN:**
The server works correctly for both SSH and HTTP traffic.

**From the internet:**
The server responds only to SSH traffic. Also, it will refuse to respond to pings on all ports except 22(ssh).

I think there is something wrong in the apache config file, but I haven't been able to find anything as it's currently listening on *:80.



And ideas / thoughs?

---

### Post by dgersting on 2008-11-19
After ALOT of trial and error, I found it what was causing the issue.

For some odd reason, my router kept binding to port 80 even though it was configured to operate on 8080 for remote management.

---


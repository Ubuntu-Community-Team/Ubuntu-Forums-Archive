---
title: "Internal Hostname"
date: 2011-05-11
forum: Server Platforms
---

### Post by ChosenOreo on 2011-05-11
Hi!
I saw in the tutorial ["The Perfect Ubuntu 11.04 Server ISPConfig3"]("http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p3") that it is possible to turn the internal ip into a hostname.

Example: 192.168.1.170 -> myserver.example.com
Example: 192.168.1.128 -> aserver.inet

However, when I edit my /etc/hosts file and after i echo the name to the /etc/hostname file, it still doesn't work.

I am using Ubuntu Server 11.04 (Natty Narwal) 
- ChosenOreo

---

### Post by volkswagner on 2011-05-11
> it doesn't work

Is not very descriptive.

If you are trying to access a machine by hostname from a second LAN connected machine, the host file must be edited on the client as well as the server.

---

### Post by kevinthecomputerguy on 2011-05-12
read this
[http://woodel.com](http://woodel.com)

---


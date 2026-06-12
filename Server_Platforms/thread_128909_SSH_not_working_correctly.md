---
title: "SSH not working correctly"
date: 2006-02-12
forum: Server Platforms
---

### Post by nwatson on 2006-02-12
I'm currently running Ubuntu on my desktop box, but I'd like to be able to ssh to it. I've installed the package, and it looks like it's working fine. Port 22 is showed as open, sshd is running, and I can ssh localhost. However, trying to ssh from my Debian machine gives me "ssh: connect to host 192.168.0.11 port 22: No route to host"

Any ideas why?

---

### Post by drogoh on 2006-02-12
Your problem has nothing to do with SSH.  You need a working route from one machine to the other.  Check your network setup between both machines and make sure you can do a basic ping between the two nodes.

---

### Post by nwatson on 2006-02-13
That was it, thanks. I overlooked the fact that this box is still set up to request DHCP, so the IP wasn't right...

---


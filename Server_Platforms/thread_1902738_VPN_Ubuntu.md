---
title: "VPN Ubuntu"
date: 2011-12-31
forum: Server Platforms
---

### Post by baloo123 on 2011-12-31
I am trying to set something up on my ubuntu server where clients can login with passwords and then appear to be on the same LAN. So for example they could use VNC to connect to each other anywhere in the world. Or use file sharing protocols such as SMB and AFP. I think this would be accomplished through VPN but I am not sure. Does anyone have any ideas?

---

### Post by spynappels on 2012-01-01
A VPN solution is what is required, I'd look at running OpenVPN in bridged mode.

---

### Post by rsvancara on 2012-01-01
OpenVPN in bridged mode is a good solution.  There are tools included in the Network Manager to use OpenVPN, which makes it a nice user friendly solution.  

--
[Know  Your Linux?]("http://www.knowyourlinux.com/")

---


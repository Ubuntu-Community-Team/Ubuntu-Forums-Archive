---
title: "SCP slow download, very fast upload"
date: 2011-07-01
forum: Server Platforms
---

### Post by talltroym on 2011-07-01
This is very strange to me.  

I have a new install of Ubuntu 10.04 LTS inside a VMWare vSphere 4.0 infrastructure.  The network this is on is behind a firewall I maintain.

My Mac is on campus and is connected via SSL VPN to the firewall so I can work on the subnet that this Ubuntu virtual server is on.   I'm able to SSH and SCP between the two machines.  If I use SCP to send a 45MB file from my Mac to Ubuntu, the transfer takes about 15 seconds to complete.  If I use SCP to retrieve the same 45MB file from Ubuntu to my Mac the transfer takes 43 minutes (yes, minutes, not seconds).

I cannot find anywhere that throttling is configured to take place.  The firewall allows full access between my machine and this Ubuntu server.

I've changed the MTU on the server to 1490, but this didn't make any difference.  Ideas?

---

### Post by dtfinch on 2011-07-01
I've had bad network hardware (both cards and switches, and sometimes only in certain combinations) cause connections to be really slow in one direction.

Edit: I missed the VM part, and the VPN part. Is it also slow if you copy large files from the host? Or from another VM?

---


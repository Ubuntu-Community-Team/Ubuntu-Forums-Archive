---
title: "PPTP Routing Issues"
date: 2010-08-09
forum: Server Platforms
---

### Post by cabrey on 2010-08-09
Hi all,

I know this has probably been solved multiple times, but I've searched the forum to no avail.

I have a PPTP server setup properly with all ports forwarded correctly. A remote machine can connect and authenticate just fine. They get their IP assigned and everything. 

The problem is that no traffic is being routed through the tunnel. Or, rather it is but the server doesn't seem to handle it. In a web browser I just get an error message. 

On a windows client I ran ipconfig and found a gateway address had not been assigned through the VPN tunnel.

Could this be the problem? If so, how can I fix it?

Thank you!

---

### Post by Groodles on 2010-08-12
I'm guessing when you say,

> The problem is that no traffic is being routed through the tunnel. Or,  rather it is but the server doesn't seem to handle it. In a web browser I  just get an error message. 

You mean that the client machine can't route through the pptp server to reach other Hosts on the pptp server's network or hosts outside the pptp servers network by using it as a gateway?

If that's the case you need to tell your pptp server to forward packets.

Edit your /etc/sysctl.conf and uncomment this line (remove the # at the front)

```
#net.ipv4.conf.default.forwarding=1
```

save the file, and reboot.  Now your machine will forward packets between the pptp servers local network and its pptp interface.

---


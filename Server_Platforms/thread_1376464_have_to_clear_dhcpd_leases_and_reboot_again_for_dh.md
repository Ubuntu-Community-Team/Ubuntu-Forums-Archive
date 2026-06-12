---
title: "have to clear dhcpd leases and reboot again for dhcp to work"
date: 2010-01-09
forum: Server Platforms
---

### Post by sherl0k on 2010-01-09
I'm running into this weird problem on my Ubuntu servers, and I'm not sure of the cause. All the boxes are in an environment that is not exactly healthy - dusty, higher than average temperature. So they'll freeze up every now and then. I don't mind it. What I do mind, though, is when I reboot them DHCP doesn't work. I have to rm -f /var/lib/dhcp3/dhcpd.leases and then reboot the system AGAIN for dhcp to kick in and work. I can't just remove the file and restart dhcp, or restart networking.

Has anyone else seen this, or know what could be causing it?

edit: DHCP will work, and the clients will get an IP address, but they can't ping the main server, and TFTP timeouts happen. The leases file looks to be full, so I'm assuming it's just not clearing itself on boot. Is there a way to clear that file before DHCP is started? using /etc/rc.local perhaps? or a cron?

---


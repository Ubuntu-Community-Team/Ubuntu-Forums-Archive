---
title: "server v12.4.1 isc-dhcp-server not working properly"
date: 2012-09-29
forum: Server Platforms
---

### Post by TomB19 on 2012-09-29
I was running Kubuntu 12.4.1 as a server (same as my clients) and it was generally fine but would crash too frequently after updates so I just switched to server 12.4.1.  It has already been a breath of fresh air because it took updates perfectly a couple of times.

... but I'm having trouble with isc-dhcp-server.

- I've added the only server interface to /etc/default/dhcp.
- copied over a known working /etc/dhcp/dhcpd.conf

restarted it but the clients can no longer see the server.

```
Sep 29 13:23:36 diniz dhcpd: DHCPOFFER on 172.16.1.63 to 6c:62:6d:dc:c8:b3 via eth0
Sep 29 13:23:36 diniz dhcpd: DHCPDISCOVER from 6c:62:6d:dc:c8:b3 via eth0
Sep 29 13:23:36 diniz dhcpd: DHCPOFFER on 172.16.1.63 to 6c:62:6d:dc:c8:b3 via eth0
Sep 29 13:23:36 diniz dhcpd: DHCPDISCOVER from 6c:62:6d:dc:c8:b3 via eth0
Sep 29 13:23:36 diniz dhcpd: DHCPOFFER on 172.16.1.63 to 6c:62:6d:dc:c8:b3 via eth0

```

It looks like offers are going out but the client does not see them.  This seems very strange to me.  I know this config was working on the old system as it gets daily use from a half dozen clients every day.

There is no firewall on this server.

Any ideas would be appreciated.

---

### Post by TomB19 on 2012-09-29
I will add that I also did a hardware swap at the same time.  I swapped an old dual core Athlon 64 for a Fusion E450 system.

---

### Post by TomB19 on 2012-09-29
Something is blocking the packets from leaving the box.  I can see another machine requesting an address, the server responding, but the machine doesn't get the offer.

```
Sep 29 18:44:35 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:44:35 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:49:35 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:49:35 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:54:35 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:54:35 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:59:35 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 18:59:35 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 19:04:36 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 19:04:36 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 19:09:36 diniz dhcpd: DHCPREQUEST for 172.16.1.65 from 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0
Sep 29 19:09:36 diniz dhcpd: DHCPACK on 172.16.1.65 to 00:1b:a9:42:a8:ff (BRN001BA942A8FF) via eth0

```

---

### Post by TomB19 on 2012-09-29
This is embarrassing but I will share the solution in case someone else stumbles over the same issue.

It was to be a simple matter of copying over the daemon configs, reboot, and enjoy.  I've done it before.  No big deal.

This time, I forgot to copy over the /etc/hosts.allow file.  I just allow everything, since this system is behind a firewall.

---


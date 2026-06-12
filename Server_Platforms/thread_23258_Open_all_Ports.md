---
title: "Open all Ports?"
date: 2005-04-01
forum: Server Platforms
---

### Post by gregh on 2005-04-01
I am having troubl;e with vpnc, the machine os dual boot and connects under windows so I know there is not communication issues.
However, I want to completely disable any port (tcp and udp) restrictions to test this under ubuntu.
Where are the default settings (IPtables?) and how can I quickly open everything?

Regards,

-Greg

---

### Post by kagou on 2005-04-01
By defaults all ports are open ! You must ensure that your client/server listen on the right interface, and wich port it use.

---

### Post by NemoTheLobster on 2005-04-01
I don't think vpnc creates any routes by default.  Make sure you have a "Target networks" line in your /etc/vpnc/<profile>.conf file.  You can check the routes by typing "ip route" at a prompt.  You should see some routes to the tun0 interface.

I had some weird routing issues when using vpnc, but they could be problems on the VPN concentrator and not on the client.  It wouldn't work at first, but after a few minutes it'd start working.  Never figured out exactly what was happening though.

---


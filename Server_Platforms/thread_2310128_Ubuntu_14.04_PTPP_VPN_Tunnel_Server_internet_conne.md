---
title: "Ubuntu 14.04 PTPP VPN Tunnel Server internet connection issue.. PLEASE HELP"
date: 2016-01-16
forum: Server Platforms
---

### Post by colbykz on 2016-01-16
I am currently trying to set up a Ubuntu PTPP VPN Server.

 I am able to get my client pc, running Windows 10, to connect to the VPN server, the pc even claims to have an internet connection, but when I attempt to use my web browser there is no web connection... interestingly enough, the client pc can still use TeamViewer to remotely manage the Ubuntu VPN Server.

 Best I can tell this is not a DNS issue, the client pc can ping IP addresses beyond the VPN network while connected to the VPN, I can ping 74.125.224.72 (google), but I cannot connect to [http://74.125.224.72/](http://74.125.224.72/) via my web browser.

 Thanks in advance for reading this, I'm new to Linux so I'm not entirely sure what log's I should post or that are relevant, and I am more than willing to furnish anything needed.

 -Colby

---

### Post by darkod on 2016-01-16
Did you enable forwarding on the vpn (ubuntu) server?

---

### Post by colbykz on 2016-01-16
I'm not entirely sure? how would I check?

---

### Post by darkod on 2016-01-16
To allow ubuntu server to forward traffic through interfaces (in your case the physical eth0 interface and the vpn tunnel ppp/tun interface), you need two things:
1. To enable ip forwarding in /etc/sysctl.conf. Open the file for editing (you need sudo rights) and remove the # character in front of the line saying like 'net.ipv4.ip_forward=1'. Save and close the file. Reboot.

2. To enable masquerading option in iptables so that returned traffic knows "where to go". You can do that temporarily with:
```
sudo iptables -t nat -A POSTROUTING -j MASQUERADE
```

If that helped, you will only need to make that iptables rules permanent and you're good to go...

---


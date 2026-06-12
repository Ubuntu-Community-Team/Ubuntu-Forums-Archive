---
title: "Serval (SERP5) Wireless Network Does Not Refresh"
date: 2010-01-24
forum: System76 Support
---

### Post by jpongin on 2010-01-24
Hi,

I upgraded to Karmic a while back with no problems.  Everything works accept for the typical disabling the modem software to enable audio.

However, I noticed that this problem was even present in Hardy.

Environment:
SERP5 wirelessly connected to a Netgear router via 802.11 N.

Steps to reproduce:
1.  Laptop is successfully connected to 802.11 N network.
2.  Netgear 802.11 N disappears (Router needs to be restarted)
3.  Netgear 802.11 N restarts, and other laptops are able to reconnect, however SERP 5 does not see the specific 802.11N network.  Other networks are visible though.
4.  I "disable wireless", and then "re-enable wireless" via the checkbox options in the icon tray.
5.  No networks re-appear.  None.  I now "disable network" and "enable network" via checkbox options in icon tray.
6.  No wireless networks appear.  I'm forced to use the wired connection.
7.  I perform the following command: sudo iwlist wlan0 scan
8.  I get the following response
wlan0    Failed to read scan data : Resource temporarily unavailable

My only option is to restart the laptop, and need to setup my entire work space again.

Is this a known issue?  And if so, what is the solution?

---

### Post by thomasaaron on 2010-01-25
Try deactivating and re-activating the adapter with...

```
sudo wlan0 eth0
sudo wlan0 eth0
```

To request an IP from a DHCP server, you can run...

```
sudo dhclient wlan0
```

We're not getting those symptoms on our shop access point, but it's a well-known issue in Ubuntu in general with some hardware/AP combinations.

---

### Post by jpongin on 2010-02-01
Thanks Thomas.  I'll try it out the next time this happens!

---


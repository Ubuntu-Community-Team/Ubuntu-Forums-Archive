---
title: "How to setup dhcp3-server with a large number vlans/subnets ?"
date: 2009-12-03
forum: Server Platforms
---

### Post by EddieX on 2009-12-03
Hi,

I have a gateway installation which handles VLAN-tagged traffic for about 1600 VLAN's and it works just fine. The VLAN's are structured by 172.xx.yy.zzz where XX+YY gives us the VLAN number (XX in interval 16-31 and YY in interval 1-99).

**Problem:**All the VLAN's should now have a DHCP-server and I have tried to setup one (dhcp3-server) by simply doing the following config:

**dhcpd.conf *(showing config for VLAN 3149)*:**
```

subnet 172.31.49.0 netmask 255.255.255.0 {
  range 172.31.49.100 172.31.49.250;
  option routers 172.31.49.1;
}
.....(one for each VLAN that should have DHCP)....

```

The *INTERFACES* variable in the /etc/default/dhcp3-server is set to "" and when I start the dhcp-server using ~500 VLAN's in the dhcpd.conf it works fine but when I increase the number of VLAN's it seems to stop working. The logs for the DHCP-server does not show any errors at all and the service is running.

I have investigated the traffic with Wireshark and it's clear that the dhcp-server does not respond to the DHCP DISCOVER packets when the dhcpd.conf contains a large number of subnets.

Am I doing something wrong or is this scenario crazy?

Ideas:
[LIST]
[*]Multiple instances of dhcp3-server (bound to interfaces) ?
[*]A single instance but several so called dhcp relay agents on each VLAN interface?
[/LIST]

All suggestions are welcome! :-)

Thanks in advance!

Best regards,
Eddie

---


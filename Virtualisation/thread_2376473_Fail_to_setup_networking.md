---
title: "Fail to setup networking"
date: 2017-11-02
forum: Virtualisation
---

### Post by satimis on 2017-11-02
Hi all

Host - Ubuntu 16.04 desktop
Guest - CentOS 7 Gnome desktop
Virtualizer - KVM

I fail to setup networking.  Please advise where can I find a relevant document for its configuration?  Thanks


ERROR
======
# systemctl restart network.service```

Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe" for details.

```

# systemctl status network.service```

&#9679; network.service - LSB: Bring up/down networking
   Loaded: loaded (/etc/rc.d/init.d/network; bad; vendor preset: disabled)
   Active: failed (Result: exit-code) since Fri 2017-11-03 08:17:52 HKT; 45s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3409 ExecStart=/etc/rc.d/init.d/network start (code=exited, status=1/FAILURE)
   CGroup: /system.slice/network.service
           &#9492;&#9472;1056 /sbin/dhclient -1 -q -lf /var/lib/dhclient/dhclient-657ef9b...

Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 network[3409]: RTNETLINK answers: File e...
Nov 03 08:17:52 centos7-gnome-pc1b00 systemd[1]: network.service: control pr...1
Nov 03 08:17:52 centos7-gnome-pc1b00 systemd[1]: Failed to start LSB: Bring ....
Nov 03 08:17:52 centos7-gnome-pc1b00 systemd[1]: Unit network.service entere....
Nov 03 08:17:52 centos7-gnome-pc1b00 systemd[1]: network.service failed.
Hint: Some lines were ellipsized, use -l to show in full.

```

# cat /etc/sysconfig/network-scripts/ifcfg-eth0```

BOOTPROTO=none
ONBOOT=yes
BROADCAST=192.168.8.255
NETWORK=192.168.8.0
NETMASK=255.255.255.0
IPADDR=192.168.8.6
USERCTL=no
BRIDGE-br0

```

# cat /etc/sysconfig/network-scripts/route-br0
an empty file

# cat /etc/sysconfig/network```

# Created by anaconda
NETWORKING=yes
HOSTNAME=centos7-gnome-pc1b00
GATEWAY=br0

```

# cat /etc/sysconfig/network-scripts/ifcfg-br0
an empty file

Host
====
&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers 218.102.32.172 219.76.98.90

# The primary network interface
auto enp2s0
iface enp2s0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.3
        dns-nameservers 218.102.32.172 219.76.98.90
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    enp2s0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Having tried changing br0 to enp2s0 with same result.

Regards
satimis

---

### Post by TheFu on 2017-11-02
Not an ubuntu question. Wrong forum.

---


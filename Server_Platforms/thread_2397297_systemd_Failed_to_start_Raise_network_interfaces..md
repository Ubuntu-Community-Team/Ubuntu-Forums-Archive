---
title: "systemd: Failed to start Raise network interfaces."
date: 2018-07-27
forum: Server Platforms
---

### Post by marcus-dahlberg on 2018-07-27
Looks like pre-up tried to bring up the interface before it gets it name.




Is there anyway to delay networking.service so that kernel can assign predictable interface name first?


 systemctl status networking.service
&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-07-27 23:02:13 CEST; 9min ago
     Docs: man:interfaces(5)
  Process: 768 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 652 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCC
 Main PID: 768 (code=exited, status=1/FAILURE)


Jul 27 23:02:07 host systemd[1]: Starting Raise network interfaces...
Jul 27 23:02:07 host sh[652]: Unknown interface enxe46f13f38973
Jul 27 23:02:09 host ifup[768]: /sbin/ifup: waiting for lock on /run/network/ifstate.eno1
Jul 27 23:02:13 host ifup[768]: Unknown interface enxe46f13f38973
Jul 27 23:02:13 host systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Jul 27 23:02:13 host systemd[1]: networking.service: Failed with result 'exit-code'.
Jul 27 23:02:13 host systemd[1]: Failed to start Raise network interfaces.
 
sudo lshw -class network
 *-network DISABLED
       description: Ethernet interface
       physical id: 2
       bus info: usb@4:4
       logical name: enxe46f13f38973
       serial: e4:6f:13:f3:89:73
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=ax88179_178a duplex=half link=no multicast=yes port=MII promiscuous=yes speed=10Mbit/s


syslog:
Jul 27 23:02:07 host sh[652]: Unknown interface enxe46f13f38973
Jul 27 23:02:07 host kernel: [    4.227791] ax88179_178a 4-4:1.0 enxe46f13f38973: renamed from eth0

---


---
title: "isc-dhcp-server systemd unit file bug - not passing interfaces"
date: 2019-05-06
forum: Server Platforms
---

### Post by kpatz on 2019-05-06
I found a bug in the systemd unit files used to start isc-dhcp-server in 18.04.

If you look at /etc/default/isc_dhcp_server, there are interfaces entries for IPv4 and IPv6.  For example:

```

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACESv4="lan0 lan1 lan2"
INTERFACESv6="lan0 lan1 lan2"

```

However, the unit scripts look for $INTERFACES, not $INTERFACESv4 and $INTERFACESv6 to pass to dhcpd's command line.

The fix is to edit these files:

**/lib/systemd/system/isc-dhcp-server.service** - change $INTERFACES to $INTERFACESv4 in the code below:

```
# The leases files need to be root:dhcpd even when dropping privileges
ExecStart=/bin/sh -ec '\
    CONFIG_FILE=/etc/dhcp/dhcpd.conf; \
    if [ -f /etc/ltsp/dhcpd.conf ]; then CONFIG_FILE=/etc/ltsp/dhcpd.conf; fi; \
    [ -e /var/lib/dhcp/dhcpd.leases ] || touch /var/lib/dhcp/dhcpd.leases; \
    chown root:dhcpd /var/lib/dhcp /var/lib/dhcp/dhcpd.leases; \
    chmod 775 /var/lib/dhcp ; chmod 664 /var/lib/dhcp/dhcpd.leases; \
    exec dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcpd.pid -cf $CONFIG_FILE $INTERFACES'

```

So, the last line would become:

```
    exec dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcpd.pid -cf $CONFIG_FILE $INTERFACESv4'
```

Do the same in **/lib/systemd/system/isc-dhcp-server6.service** but change $INTERFACES to $INTERFACESv6, as below:

```
# The leases files need to be root:dhcpd even when dropping privileges
ExecStart=/bin/sh -ec '\
    CONFIG_FILE=/etc/dhcp/dhcpd6.conf; \
    if [ -f /etc/ltsp/dhcpd6.conf ]; then CONFIG_FILE=/etc/ltsp/dhcpd6.conf; fi; \
    [ -e /var/lib/dhcp/dhcpd6.leases ] || touch /var/lib/dhcp/dhcpd6.leases; \
    chown root:dhcpd /var/lib/dhcp /var/lib/dhcp/dhcpd6.leases; \
    chmod 775 /var/lib/dhcp ; chmod 664 /var/lib/dhcp/dhcpd6.leases; \
    exec dhcpd -user dhcpd -group dhcpd -f -6 -pf /run/dhcp-server/dhcpd6.pid -cf $CONFIG_FILE $INTERFACESv6'

```

After updating, run **sudo systemctl daemon-reload** and then restart isc-dhcp-server with **sudo systemctl restart isc-dhcp-server** and (if using ipv6) **sudo systemctl restart isc-dhcp-server6**

Is there a place I can formally report this as a bug, so it gets fixed in a future update?

---


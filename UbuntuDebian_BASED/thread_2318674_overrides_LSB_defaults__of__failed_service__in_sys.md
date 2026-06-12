---
title: "overrides LSB defaults  of  failed service  in systemd"
date: 2016-03-28
forum: Ubuntu/Debian BASED
---

### Post by luofeiyu2011 on 2016-03-28
systemctl --failed

 UNIT                    LOAD   ACTIVE SUB    DESCRIPTION
&#9679; dnsmasq.service         loaded failed failed dnsmasq - A lightweight DHCP and 
&#9679; isc-dhcp-server.service loaded failed failed LSB: DHCP server

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

2 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.

systemctl disable dnsmasq.service

Synchronizing state for dnsmasq.service with sysvinit using update-rc.d...
Executing /usr/sbin/update-rc.d dnsmasq defaults
insserv: warning: current start runlevel(s) (empty) of script `dnsmasq' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `dnsmasq' overrides LSB defaults (0 1 6).
Executing /usr/sbin/update-rc.d dnsmasq disable
insserv: warning: current start runlevel(s) (empty) of script `dnsmasq' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `dnsmasq' overrides LSB defaults (0 1 6).
systemctl disable  isc-dhcp-server.service

Synchronizing state for isc-dhcp-server.service with sysvinit using update-rc.d...
Executing /usr/sbin/update-rc.d isc-dhcp-server defaults
Executing /usr/sbin/update-rc.d isc-dhcp-server disable
insserv: warning: current start runlevel(s) (empty) of script `isc-dhcp-server' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `isc-dhcp-server' overrides LSB defaults (0 1 6).

There are two service dnsmasq.service and  isc-dhcp-server.service,failed at the boot stage, and can't be disabled.
The pc is in my home ,work as desktop or server, if no bad effect ,let me disable the two service.

---


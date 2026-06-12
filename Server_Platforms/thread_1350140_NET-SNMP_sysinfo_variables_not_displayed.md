---
title: "NET-SNMP sysinfo variables not displayed"
date: 2009-12-09
forum: Server Platforms
---

### Post by gertcronje on 2009-12-09
Hi

This is not really an Ubuntu specific query, but I hope someone may have a solution to this.

I'm developing an embedded linux device that must have SNMP  support. I've installed NET-SNMP and everyhing seems to work OK with the exception that the sysInfo variables are not displayed in the GetIF utility. It says "SysInfo Variables OK" but does not display them.

It does the same with a NET-SNMP installation on my Ubuntu 8.10 desktop machine, so it is not limited to the embedded installation.

A snmpwalk on the device does show the data:
snmpwalk -v 1 -c public 192.168.1.11 
SNMPv2-MIB::sysDescr.0 = STRING: RT Systems TM3 Unit, MB SW Ver 2.11, Webserver Ver 2.02
SNMPv2-MIB::sysObjectID.0 = OID: SNMPv2-SMI::enterprises.32278.1
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (7946) 0:01:19.46
SNMPv2-MIB::sysContact.0 = STRING: root
SNMPv2-MIB::sysName.0 = STRING: crmu
SNMPv2-MIB::sysLocation.0 = STRING: Unknown
SNMPv2-MIB::sysServices.0 = INTEGER: 10
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (3498116737) 404 days, 20:59:27.37

I apologize if this is not the correct place to post this query.

Thanks

Gert

---


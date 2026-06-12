---
title: "snmpwalk (Unknown Object Identifier) - MIB help"
date: 2011-04-21
forum: Server Platforms
---

### Post by calabaria on 2011-04-21
Hello, 

Kind of new here and need some help with snmp. I have an ubuntu system that is unable to snmpwalk 'system', 'interface', 'tcp', 'udp', and 'ip'. I'm pretty sure I'm missing the MIBS, but I can't figure out where to download them, where to put them, and how to specify them. Below is some information on this ubuntu system (mysys2) and some output from snmpwalk showing my issue. If I run the same snmpwalk command from my MacBook (mysys1) things work as expected. Thanks in advance for the help!

My ubuntu system (mysys2): 
myuser@mysys2:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

myuser@mysys2:~$ snmpwalk -c cacti-ro -v1 myhost system
system: Unknown Object Identifier (Sub-id not found: (top) -> system)

My MacBook (mysys1):
mysys1:~ myuser$ snmpwalk -c cacti-ro -v1 myhost system
SNMPv2-MIB::sysDescr.0 = STRING: Linux myhost 2.6.35-28-server #49-Ubuntu SMP Tue Mar 1 14:55:37 UTC 2011 x86_64
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (9158775) 1 day, 1:26:27.75
SNMPv2-MIB::sysContact.0 = STRING: mycontact
SNMPv2-MIB::sysName.0 = STRING: myhost
SNMPv2-MIB::sysLocation.0 = STRING: mylocation
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORID.1 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORDescr.1 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.2 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.3 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (0) 0:00:00.00
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (0) 0:00:00.00

---


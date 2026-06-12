---
title: "cfgmaker not working (MRTG)."
date: 2015-12-28
forum: Server Platforms
---

### Post by gardenair on 2015-12-28
[COLOR=#222426][FONT=Arial] i am trying to configure MRTG.My server private ip address is 10.1.83.10 and its host name is "masterdns". The problem is when i use  
[/FONT][/COLOR]```
[COLOR=#222426][FONT=Arial]# snmpwalk -v2c -c masterdns localhost system

[/FONT][/COLOR][COLOR=#222426][FONT=Arial].[/FONT][/COLOR]SNMPv2-MIB::sysDescr.0 = STRING: Linux masterdns 3.10.0-229.el7.x86_64 #1 SMP Fri Mar 6 11:36:42 UTC 2015 x86_64SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (24523) 0:04:05.23
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmp.local.conf)
SNMPv2-MIB::sysName.0 = STRING: masterdns
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (edit /etc/snmp/snmpd.conf)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORID.1 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORID.9 = OID: SNMP-NOTIFICATION-MIB::snmpNotifyFullCompliance
SNMPv2-MIB::sysORID.10 = OID: NOTIFICATION-LOG-MIB::notificationLogMIB
SNMPv2-MIB::sysORDescr.1 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.2 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.3 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORDescr.9 = STRING: The MIB modules for managing SNMP Notification, plus filtering.
SNMPv2-MIB::sysORDescr.10 = STRING: The MIB module for logging SNMP Notifications.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.9 = Timeticks: (22) 0:00:00.22
SNMPv2-MIB::sysORUpTime.10 = Timeticks: (22) 0:00:00.22

```

When i use the command

```
# snmpwalk -v2c -c masterdns localhost ssCpuRawUser.0
UCD-SNMP-MIB::ssCpuRawUser.0 = Counter32: 3115

```

[COLOR=#222426][FONT=Arial]The cfgmaker maker show me.

[/FONT][/COLOR]```
# cfgmaker  --ifref=ip --ifdesc=ip --global="Workdir: /var/www/mrtg" --global="Options[_]: growright , unknownzero , bits" --output=/etc/mrtg/pdcmrtg.cfg public@10.1.83.10

[I]**Use of uninitialized value $t in substitution (s///) at /usr/bin/cfgmaker line 1375.
Use of uninitialized value $t in substitution (s///) at /usr/bin/cfgmaker line 1376.
Use of uninitialized value $t in substitution (s///) at /usr/bin/cfgmaker line 1377.
Use of uninitialized value $fs in pattern match (m//) at /usr/bin/cfgmaker line 1382.
Use of uninitialized value $t in hash element at /usr/bin/cfgmaker line 1383.**[/I]
--base: Get Device Info on public@10.1.83.10:
--base: Vendor Id: Unknown Vendor - 1.3.6.1.4.1.8072.3.2.10
--base: Populating confcache
--base: Get Interface Info
--base: Walking ifIndex
--base: Walking ifType
--base: Walking ifAdminStatus
--base: Walking ifOperStatus
--base: Walking ifMtu
--base: Walking ifSpeed
--base: Writing /etc/mrtg/pdcmrtg.cfg
```


Please guide me that how can I solve it ?

---


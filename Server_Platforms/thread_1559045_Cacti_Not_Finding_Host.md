---
title: "Cacti Not Finding Host"
date: 2010-08-23
forum: Server Platforms
---

### Post by Drezard on 2010-08-23
Hey guys.

Got an issue with Cacti. 

I've got snmpd setup on my Ubuntu server. Its got an snmpv3 user setup on it and it can be successfully walked from the Cacti server. But cacti still registers it as being "Down". Heres the relevant bit of the logs:

> 
08/23/2010 10:10:01 AM - CMDPHP: Poller[0] WARNING: SNMP GetNext Timeout for Host:'10.232.40.6', and OID:'.1.3'
08/23/2010 10:10:01 AM - CMDPHP: Poller[0] WARNING: SNMP GetNext Timeout for Host:'10.232.40.6', and OID:'.1.3.6.1.2.1.1.3.0'
08/23/2010 10:10:01 AM - CMDPHP: Poller[0] WARNING: SNMP GetNext Timeout for Host:'10.232.40.6', and OID:'.1.3.6.1.2.1.1.1.0'
08/23/2010 10:10:01 AM - CMDPHP: Poller[0] Host[4] SNMP: Host did not respond to SNMP


I can Snmpwalk the host using the details provided. Thus, I don't understand why Cacti is throwing errors.

Any ideas?

Daniel

---


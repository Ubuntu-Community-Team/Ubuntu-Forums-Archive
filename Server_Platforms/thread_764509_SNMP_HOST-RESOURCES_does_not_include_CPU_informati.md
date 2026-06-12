---
title: "SNMP HOST-RESOURCES does not include CPU information"
date: 2008-04-23
forum: Server Platforms
---

### Post by Joel Duckworth on 2008-04-23
Hi, 

I've setup snmpd on my server, however it appears that CPU information is not being returned. 

I'm running ```
snmpwalk -v 2c -c <community> host|less
``` to check for the results that are returned. The HOST-RESOURCES results does not include any cpu information.

My snmpd.conf has the following. How do mibs get mapped to system resources? Is this a flaw in the package setup or in my local configuration? How do I get the HOST-RESOURCES section to map the CPU information to the hrProcessorTable section in the mib?

```

... other com2sec lines
com2sec readonly localhost <community>
com2sec paranoid  default         public
group MyROSystem v1        paranoid
group MyROSystem v2c       paranoid
group MyROSystem usm       paranoid
group MyROGroup v1         readonly
group MyROGroup v2c        readonly
group MyROGroup usm        readonly
group MyRWGroup v1         readwrite
group MyRWGroup v2c        readwrite
group MyRWGroup usm        readwrite
view all    included  .1                               80
view system included  .iso.org.dod.internet.mgmt.mib-2.system
access MyROSystem ""     any       noauth    exact  system none   none
access MyROGroup ""      any       noauth    exact  all    none   none
access MyRWGroup ""      any       noauth    exact  all    all    none
syslocation Unknown (configure /etc/snmp/snmpd.local.conf)
syscontact Root <root@localhost> (configure /etc/snmp/snmpd.local.conf)
```

---


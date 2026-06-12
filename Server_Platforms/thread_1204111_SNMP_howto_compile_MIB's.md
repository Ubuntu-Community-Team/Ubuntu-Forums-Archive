---
title: "SNMP howto compile MIB's"
date: 2009-07-04
forum: Server Platforms
---

### Post by Cloze on 2009-07-04
Hallo,

I want to read out a specific parameter of a device via SNMP. I can read information through an snmpwalk, but then I get all information available off that device. (snmpwalk -c public -v 1 172.16.10.10). 

So i want to do a snmpget of a specific parameter of my device. (snmpget -c public -v1 172.16.10.10 <parameter>) 
Before I can use the parameters i must compile the mib file included with the device. But i don't know how to compile or add mibs to  ubuntu. I didn't find anything on the Internet how to do so. Can sombody help me out?

---

### Post by Cloze on 2009-07-04
I can't even retrieve information via snmpget even when using an OID.
example: snmpget -c public -v1 172.16.10.10 1.3.6.1.4.1.12394.1.1.1.
After hitting this command i get this:
Error in packet
Reason: (noSuchName) There is no such variable name in this MIB.
Failed object: SNMPv2-SMI::enterprises.12394.1.1.1

---

### Post by Cloze on 2009-07-04
Problem solved

> 
Step 1 Add your mib file to the correct folder
cp MY-MIB.txt /usr/local/share/snmp/mibs

Step 2 Add mibfile to tools
export MIBS=+MY-MIB

==> exporting must be done everytime when rebooting


---


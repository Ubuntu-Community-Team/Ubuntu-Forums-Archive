---
title: "Execut script with snmp"
date: 2010-02-26
forum: Server Platforms
---

### Post by BarreSwe on 2010-02-26
Hi,

Trying to read a script result through a snmp get command, it works just fine if I create the following line in /etc/snmp/snmpd.conf
```
exec testing /bin/echo hello world
```the result from an snmpwalk is this
```
$ snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.2021.8
UCD-SNMP-MIB::extIndex.1 = INTEGER: 1
UCD-SNMP-MIB::extNames.1 = STRING: testing
UCD-SNMP-MIB::extCommand.1 = STRING: /bin/echo
UCD-SNMP-MIB::extResult.1 = INTEGER: 0
UCD-SNMP-MIB::extOutput.1 = STRING: hello world
UCD-SNMP-MIB::extErrFix.1 = INTEGER: noError(0)
UCD-SNMP-MIB::extErrFixCmd.1 = STRING: 

```But when I try to specify a different OID
```
exec .1.3.6.1.4.1.20294.8 testing /bin/echo helo world
```I get this result
```

$ snmpwalk -v 2c -c public localhost .1.3.6.1.4.1.20294.8
SNMPv2-SMI::enterprises.20294.8 = No Such Object available on this agent at this OID

```What am I doing wrong?

INFO
```
$ uname -a && snmpd -v
Linux homer 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

NET-SNMP version:  5.4.1
Web:               http://www.net-snmp.org/
Email:             net-snmp-coders@lists.sourceforge.net

```

---


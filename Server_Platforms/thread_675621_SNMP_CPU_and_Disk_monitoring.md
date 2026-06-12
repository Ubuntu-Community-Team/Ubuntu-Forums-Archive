---
title: "SNMP CPU and Disk monitoring"
date: 2008-01-22
forum: Server Platforms
---

### Post by ybjones@sgti.net on 2008-01-22
I have installed snmpd but I can't get CPU or disk information. Trying: 

snmpget -v 2c -c public localhost .1.3.6.1.2.1.25.3.3.1.2

returns: 

HOST-RESOURCES-MIB::hrProcessorLoad = No Such Object available on this agent at this OID

It is the same when looking for disk or memory information. I want to use SNMP for this for managed services testing. Can anybody point me in the right direction or provide some instructions. I have searched but haven't found anything that helps.

Thanks.

---

### Post by HermanAB on 2008-01-23
[http://www.zabbix.com/](http://www.zabbix.com/)

Cheers,

Herman

---

### Post by ybjones@sgti.net on 2008-01-23
Am I missing something here? How does Zabbix give me access to CPU/Disk/Memory information through SNMP?

---

### Post by HermanAB on 2008-01-23
Zabbix has its own client (agent).  Install the Zabbix agent and everything just magically works.  It is the easiest SNMP system ever.

Cheers,

Herman

---

### Post by ybjones@sgti.net on 2008-01-23
I have my own monitoring tool so that is why I want SNMP rather than something like Zabbix.

---

### Post by ybjones@sgti.net on 2008-01-29
So is there anybody using SNMP to monitor CPU and disk usage?

---

### Post by The Cog on 2008-01-31
For storage (memory and disk) look at the hrStorageTable 1.3.6.1.2.1.25.2.3
or the UCD diskio table 1.3.6.1.4.1.2021.13.15.1.1.2000002780
and UCD memory table 1.3.6.1.4.1.2021.4.2000003823
For CPU you cold try the UCD SystemStats table 1.3.6.1.4.1.2021.11.2000003826

Those last numbers look wrong to me but that's what I see in this package here.
HTH

---

### Post by faheyd on 2008-05-24
> **ybjones@sgti.net said:**
> I have installed snmpd but I can't get CPU or disk information. Trying: 

snmpget -v 2c -c public localhost .1.3.6.1.2.1.25.3.3.1.2

returns: 

HOST-RESOURCES-MIB::hrProcessorLoad = No Such Object available on this agent at this OID

It is the same when looking for disk or memory information. I want to use SNMP for this for managed services testing. Can anybody point me in the right direction or provide some instructions. I have searched but haven't found anything that helps.

Thanks.

Sometimes, I use the oid above it to see what all is supporting on my 'node':
snmpwalk -v 2c -c public localhost .1.3.6.1.2.1.25.3
and if you need to oids:
snmpwalk -O n -v 2c -c public localhost .1.3.6.1.2.1.25.3

This should get you on your way.  I've noticed on Ubuntu, with every release, some things either start working or just break as far as snmp oids go. I got tired of looking for answers. If it's a production system and you find something that finally works, don't update it (except for security).

Also, on the other oids to look at:
snmpwalk -v 2c -c public localhost dsk
 snmpwalk -O n -v 2c -c public 10.66.66.66 dsk

Hmm, I just looked specifically at what you were asking and I see the same thing:
$ snmpwalk -v 2c -c public (mylocalipaddress) .1.3.6.1.2.1.25.3.3.1.2
HOST-RESOURCES-MIB::hrProcessorLoad.768 = INTEGER: 100
$ snmpget -v 2c -c public (mylocalipaddress) .1.3.6.1.2.1.25.3.3.1.2
HOST-RESOURCES-MIB::hrProcessorLoad = No Such Instance currently exists at this OID

I don't know what to say.  Works with snmpwalk, but does not with snmpget .

---


---
title: "Stopping 10.04's snmpd from filling up syslog"
date: 2010-08-12
forum: Server Platforms
---

### Post by simonpt on 2010-08-12
When building 8.04 servers, I reconfigure snmpd's logging options to prevent copious low priority messages being logged whenever our network management workstation polls them. I edit /etc/default/snmpd and change line 11 from:
 
```
SNMPDOPTS='-Lsd -Lf /dev/null ...'
```
 
to:
 
```
SNMPDOPTS='-LS 0-4 d -Lf /dev/null ...'
```
 
I think I originally found this tip [here]("http://www.speedyturtle.info/blog/?p=62").
 
I'm trying the same change on a 10.04 server but snmpd doesn't like the syntax of the change. I've tried to make sense of the documentation, and I've tried different variants (-Ls4d, -Ls0-4d, -Lsd -LE4, -Lsd -LE0-4), all of which pass the syntax checking but don't reduce the level of logging.
 
Can someone please tell me how to correctly reconfigure 10.04's snmpd to only log messages with priorities 0 thru 4 to syslog?

---

### Post by thctlo on 2010-08-28
if you had read the "tip" site you gave. 
 
you have read :
for ubuntu 9.04 ..  
The fix was to modify the following line in my /etc/default/snmpd file:
Before:
SNMPDOPTS=’-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0&#8242;
After:
SNMPDOPTS=’-LS4d -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0&#8242;
Once this is done restart snmpd: sudo /etc/init.d/snmpd restart
 
just did this myself and it worked
 
and on the site .. 
Update:
I checked on my Ubuntu 8.04 server (64bit) 
my /etc/default/snmpd :
SNMPDOPTS=’-LS 0-4 d -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0&#8242;
 
the last one is with old predicated options, which do not work on 10.04. 
 
try the SNMPDOPTS=’-LS4d .... and you see it wil work.

---

### Post by simonpt on 2010-09-07
Using '-LS4d' helps a bit. I no longer get these log entries:
 
```
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4409->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4407->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4409->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4407->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4409->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4407->[10.0.10.30]
Sep 7 17:06:47 cms1 snmpd[710]: Connection from UDP: [10.10.1.29]:4409->[10.0.10.30]

```
 
But I still get these ones, which I can normally suppress under 8.04:
 
```
Sep 7 17:11:47 cms1 snmpd[3717]: send response:
Sep 7 17:11:47 cms1 snmpd[3717]: -- HOST-RESOURCES-MIB::hrStorageType.1
Sep 7 17:11:47 cms1 snmpd[3717]: -- HOST-RESOURCES-MIB::hrStorageDescr.1
Sep 7 17:11:47 cms1 snmpd[3717]: send response:
Sep 7 17:11:47 cms1 snmpd[3717]: -- HOST-RESOURCES-MIB::hrStorageAllocationUnits.36
Sep 7 17:11:47 cms1 snmpd[3717]: -- HOST-RESOURCES-MIB::hrStorageSize.36
Sep 7 17:11:47 cms1 snmpd[3717]: -- HOST-RESOURCES-MIB::hrStorageUsed.36

```
 
Any idea how to suppress these ones too?

---


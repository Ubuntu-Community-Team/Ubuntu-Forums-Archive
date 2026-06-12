---
title: "[SOLVED] snmpd won't respond to outside requests"
date: 2008-03-10
forum: Server Platforms
---

### Post by MatsB on 2008-03-10
I have a new installed Ubuntu server 7.10 on 64bit platform no firewall installed or in the way and just installed snmpd with ```
 apt-get install snmpd
```

Running snmpwalk locally works just fine
```
snmpwalk -v 2c -c public 127.0.0.1 versiontag
UCD-SNMP-MIB::versionTag.0 = STRING: 5.3.1
```

...but when i run from another Linux server (on the same local LAN) i get Timeout: No Response from x.x.x.x


My /etc/snmp/snmpd.conf file:
```
 ###########################################################################
#
# snmpd.conf
#
#   - created by the snmpconf configuration program
#
###########################################################################
# SECTION: System Information Setup
#
#   This section defines some of the information reported in
#   the "system" mib group in the mibII tree.

# syslocation: The [typically physical] location of the system.
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysLocation.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  location_string


# syscontact: The contact information for the administrator
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysContact.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  contact_string



###########################################################################
# SECTION: Access Control Setup
#
#   This section defines who is allowed to talk to your running
#   snmp agent.

# rocommunity: a SNMPv1/SNMPv2c read-only access community name
#   arguments:  community [default|hostname|network/bits] [oid]

rocommunity  public
```

---

### Post by MatsB on 2008-03-10
Solution was to edit the /etc/default/snmp file

from this
```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'
```

to this
```
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 0.0.0.0'
```

---


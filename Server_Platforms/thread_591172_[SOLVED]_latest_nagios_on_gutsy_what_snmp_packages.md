---
title: "[SOLVED] latest nagios on gutsy what snmp packages?"
date: 2007-10-25
forum: Server Platforms
---

### Post by inphektion on 2007-10-25
I have the latest nagios installed on gutsy and am trying to use the check_snmp plugin but is isn't installed.  From the guide...
> The check_snmp plugin will only get compiled and installed if you have the net-snmp and net-snmp-utils packages installed on your system.
so what package is equivalent to that for ubunutu?  Libsnmp-base?    I don't see any snmp package for ubuntu with the word "utils" in it?

---

### Post by inphektion on 2007-10-25
ok i installed libsnmp-base and dev and rebuilt and still didn't see plugin.  then just installed snmp and now the plugin is there... yay.:popcorn:

---


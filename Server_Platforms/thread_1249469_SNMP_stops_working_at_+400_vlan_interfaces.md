---
title: "SNMP stops working at +400 vlan interfaces"
date: 2009-08-25
forum: Server Platforms
---

### Post by Jeroeneman on 2009-08-25
Hi y'all,

We're using Ubuntu Hardy in the product my company makes. One of the usages is an Ubuntu server which has in some cases up to 500 vlan interfaces. For some reason the SNMP daemon on the box stops responding during startup. We noticed the failure of the SNMP agent when the number of virtual interfaces reached over more then 400 interfaces.

When analysing the strace log file, you can see 2 things happening:
* interface names get cut off after 8 characters ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=468260](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=468260)). We installed the snmpd package with the bugfix, but still no luck.
* the snmp daemon keeps searching for an interface with the name '80' (see strace log)

All qlbrxxxxx interfaces you'll find in the strace output are L2 bridge interfaces.
Lowering the number of interfaces is only a last resort approach as we really need SNMP for the monitoring of the servers. Actually we don't need any information/statistics on the virtual interfaces, so if there is a way to let the SNMPd ignore all these interfaces, please let me know how.
To stop the agent, you'll have to use kill -9. It no longer responds to regular kills or init.d scripts.

SNMP strace log: [http://86.39.164.37/snmp-strace.txt](http://86.39.164.37/snmp-strace.txt) (50MB - filled in less then a minute)

Thanks in advance for reading this and if you need more information, I'll be glad to provide you with any. Sorry if this post would be in the wrong forum.

---


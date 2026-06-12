---
title: "Snmp mib"
date: 2010-09-20
forum: Server Platforms
---

### Post by markvdm on 2010-09-20
Hi Guys
 
Hope someone can assist me as I'm really stuck on this problem.
 
I am running Zabbix 1.8.3 monitoring tool on Ubuntu Server 10.04. Everything is running beautifully, except for SNMP. Now I can run snmpwalk etc and I am getting valid data, but the problem comes in when trying to tie this up to a MIB file. I have copied the MIB file into the directory where all other MIB files are stored, but I'm still getting an error stating that the MIB is not found.
 
Am I missing a step or is the MIB file incorrect?

---

### Post by The Cog on 2010-09-20
I'm not familiar with Zabbix. You may need to get it to compile the mib before it can use it.

Another possibility is that the MIB extends / refers to another MIB which you haven't installed. Have a look at the MIB file and check that you have all the other mibs that it lists in the **imports** list.

---


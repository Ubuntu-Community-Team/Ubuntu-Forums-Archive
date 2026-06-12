---
title: "Ubuntu Jaunty Jackalope(9.04) Server--Running Nagios"
date: 2009-06-04
forum: Server Platforms
---

### Post by Jago6060 on 2009-06-04
I think the title pretty much says what this is about but I'll give a list for clarification.

Ubuntu 9.04 Server
-All needed services running
-All current updates
-Hosting VMware Server 2 running one virtual machine
-Running Nagios 3 and Nagios Plugins 1.4

Question/Problem:  I need to get Nagios to monitor printer traffic as a test before it goes into production at my company.  Its currently just monitoring the host server but will eventually be implemented to monitor UPS devices.  This requires the use of SNMP and as I understand it, Ubuntu 9.04 has an SNMP equivalent.  This is a problem because  Nagios looks for net-snmp and net-snmp-utils which as mentioned, are aliased in Ubuntu 9.04.  Is there any way to get the net-snmp and net-snmp-utils packages installed and running, or am I better off trying to point Nagios to the Ubuntu SNMP packages?

P.S.  I'm fairly new to Nagios

---

### Post by Jago6060 on 2009-06-05
anyone?

---

### Post by rmiley on 2009-06-14
Did you get this solved?
 
I am having the same problem.
 
Thanks.

---

### Post by Jago6060 on 2009-06-15
No solution yet.  I found something in reference to monitoring UPS devices, but it involves grabbing OID's and MIB's or something, way beyond my range of expertise.  I would think that Nagios, being enterprise grade, would have a simple solution.

---

### Post by Jago6060 on 2009-07-17
(sorry for the delay)Problem solved:  Downloaded net-snmp and a perl script(check_apcups) that works as a plugin for nagios.  The script has all the oids needed for ups devices build in, so its a simple copy and paste.

---


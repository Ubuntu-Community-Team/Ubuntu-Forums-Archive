---
title: "64-bit disk MIB for SNMP"
date: 2013-01-03
forum: Server Platforms
---

### Post by Obi-Wan-YJ on 2013-01-03
I'm running a fresh 64-bit install of 12.10.  It's the desktop edition, but I do run some server apps on the box, including SNMP.

I'm trying to use mrtg & net-snmp to monitor (among other things) disk usage on the box.  The stock SNMP only has the 32-bit dskTable MIB, and my /home filesystem is up around 4TB, which is nearly double what a 32-bit integer can handle.

I've read about the 64-bit extension to the dskTable MIB, which includes the entries dskTotalLow and dskTotalHigh, which combine to support 64-bit values.  I've downloaded the MIB into /usr/share/mibs/netsnmp and restarted snmpd, but snmpwalk still isn't recognizing the new variables.

How do I get snmpd to provide the new variables that support 64-bit disk usage?

---

### Post by Obi-Wan-YJ on 2013-01-03
<sigh>

It looks like the 64-bit extensions didn't appear in net-snmp until v5.5, which was released in July 2012.  The most recent version is 5.7.
  [http://www.net-snmp.org/about/ChangeLog.html](http://www.net-snmp.org/about/ChangeLog.html)

12.10 still ships with v5.4.3.  Is there a pre-built deb out there for 5.5 or newer, or am I stuck building it from source?

---


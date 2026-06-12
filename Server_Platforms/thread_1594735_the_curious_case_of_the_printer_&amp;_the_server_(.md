---
title: "the curious case of the printer &amp; the server (printing reboots server)"
date: 2010-10-12
forum: Server Platforms
---

### Post by mowgliee on 2010-10-12
on lucid 10.04 every time a client on the LAN prints OR i restart printer (via power switch), it reboots the server!

on hardy 8.04 the first print job of the day does the same, but later print jobs do not.

anyone have any clue?  this is beyond crazy to me.

specs/details:
all clients on lucid.

applies to different printers of different brands. printers do go into sleep mode after 2 hrs of non use (perhaps why 8.04 reboots only w/ 1st print job?).  printers get static pvt ip from server based on mac.

8.04 used to work just fine; replaced that server w/ 10.04, symptoms above occurred, put 8.04 server back, symptoms above occur.

using cups for printing.

servers also do dhcp, ldap, dns, routing/nat btwn public & pvt networks (have 2 nics), but all of that works fine.

cant provide any log file transcripts b/c servers reboot immediately, so no entries in log files.  ugh.

all else same as when everything used to work (switches, isp, cabling, etc), so i'm ruling those out as factors.

any ideas or you as baffled as i am?

---

### Post by mowgliee on 2010-10-17
update:

on 10.04 i notice the server reboots when i turn the printer on, not off.

on 8.04 i notice the server reboots when the printer comes out of sleep mode.  if the printer is not in sleep mode, it prints w/o rebooting the server.

i thought it had to do w/ the printer asking the server for a dhcp IP but the printer has that always (i can go to [http://printerIP](http://printerIP) even when printer is in sleep mode).

so i'm still baffled, what the heck is going on?

---


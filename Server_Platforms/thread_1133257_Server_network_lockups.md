---
title: "Server network lockups"
date: 2009-04-22
forum: Server Platforms
---

### Post by beazer on 2009-04-22
Hi All

We are getting intermittent network hangs on Ubuntu server 8.04 AMD64.  The server has an Intel server motherboard with a Xeon CPU, and Intel 82566DM-2 / 82541GI Nics on the motherboard

When this happens, we cannot ssh in to the server.  The server is remote and headless so we don't have access to the console.

About once a month or so, the network seems to lock up on the server.  Sometimes the server recovers by itself, bust mostly we have to power cycle the server.

There is nothing obvious in syslog or dmesg, but most processes seem to be running and logging OK.  Processes that require network access show timeout messages.

The server responds to pings.

Once it goes into this state, we cannot access the machine via ssh, Samba, SMTP or IMAP

Munin shows no resource issues before the hang, but does not record any data during the hang.  Nagios NRPE continues to run, but times out trying to send the data back to the Nagios console.

We have also seen this behaviour on a different server at a different site with Ubuntu server 7.10 i386, but we haven't seen it since it was updated to Ubuntu server 8.04 i386.  This is an Intel motherboard with a Core 2 Duo CPU

Any ideas of what may be causing it, or any suggestions for troubleshooting would be welcome.

Thanks 
Rob

---

### Post by kvizz on 2009-04-23
i've had this issue about a year ago, the problem was in mysql. something with tables being locked, don't remeber exactly. converting db from MyIsam to InnoDb was helpful for me.

---


---
title: "[SOLVED] supressing entrys in syslog-ng logfile"
date: 2007-12-16
forum: Server Platforms
---

### Post by MatsB on 2007-12-16
My Netgear FW is spamming my syslog-ng logfile with these rows:
Dec 16 15:18:46 192.168.0.1 kernel: [2007 Dec 16 15:18:47] FVS338 LOG_PACKET
Dec 16 15:18:46 192.168.0.1 kernel: [2007 Dec 16 15:18:47] FVS338 LOG_PACKET



I've activated "Log all unicast traffic" in my Netgear FW and that's what sending all those log entrys. I don't want do deactivate the function so 
Is there anyway I can supress these entrys in syslog-ng when they are sen't to my log file? At the moment the logfile is growing large quickly.

---

### Post by lwoodtri on 2007-12-17
Hi,

you will need to create a  filter that uses a "not match" criteria that will filter that specific error message, and apply that filter to the destination log file.

cb

---

### Post by MatsB on 2007-12-17
Thx for the reply,

This seemed to solve it:
filter logpacket  { not match("LOG_PACKET"); };


destination df_fw { file("/var/log/fw.log"); };

log {
        source(network);
        destination(df_fw);
	filter(logpacket);
};

---


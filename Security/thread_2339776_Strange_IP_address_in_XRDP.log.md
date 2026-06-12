---
title: "Strange IP address in XRDP.log"
date: 2016-10-12
forum: Security
---

### Post by Vladislav_Roussino on 2016-10-12
I'm trying to investigate why sometimes when i reestablish a remote desktop connection to my Ubuntu server running 14.04 i only get a grey screen and i found something strange in my xrdp.log. I have multiple lines like the following:

```
Oct 12 13:37:39 g8 XRDP[25873]: (25873)(140702267578176)[INFO ] An established connection closed to endpoint: NULL:NULL - socket: 8
Oct 12 13:37:39 g8 XRDP[25873]: (25873)(140702267578176)[DEBUG] xrdp_mm_module_cleanup
Oct 12 13:37:39 g8 XRDP[25873]: (25873)(140702267578176)[INFO ] An established connection closed to endpoint: 109.112.47.46:12148 - socket: 12
Oct 12 13:37:39 g8 XRDP[25873]: (25873)(140702267578176)[INFO ] An established connection closed to endpoint: NULL:NULL - socket: 13
Oct 12 13:37:39 g8 XRDP[25873]: (25873)(140702267578176)[ERROR] Listening socket is in wrong state we terminate listener

```

the IP and the port are always the same. the strange thing is that this is not my IP - nmap scan returns nothing for it. Judging by the range it's based in Italy, which is also strange because i have nothing to do with Italy.

Port 12148 is closed at my side. I have only ports 21,22 and 80 open and i have secured 22 by an encrypted key. When i need rdp connection outside my home network i tunnel it through port 22, so i have all my other ports closed besides the mentioned above 21,22 and 80.

I cannot find any related entries for this IP in my auth.log file.

What might be this? Do i need to be concerned about those entries in my xrdp.log?

---

### Post by bashiergui on 2016-10-18
Looks like it was a bug in xrdp that was fixed recently. Updating xrdp should fix it. [https://github.com/neutrinolabs/xrdp/issues/381](https://github.com/neutrinolabs/xrdp/issues/381)

---


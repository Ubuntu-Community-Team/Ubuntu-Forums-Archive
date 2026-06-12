---
title: "/var/log/samba logs"
date: 2006-11-01
forum: Server Platforms
---

### Post by acgiglyph on 2006-11-01
I noted that in my /var/log/samba directory there are machines that are listed with empty log files.  My guess is that the machines are looking for a printer on the network and these logs appear as a result of there network scan, however if anyone can help me as to why these empty log files are created I would appreciate it.

I note that one machine does have the following entry in the log file.
[2006/11/01 12:00:30, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 12:00:30, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 12:32:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 12:32:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 13:04:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 13:04:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 13:36:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2006/11/01 13:36:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!

---

### Post by ykhun on 2007-02-12
In your samba conf at the printer section, do the following and restart smbd

```
   printcap name = /dev/null
   load printers = no
```

---

### Post by usererror on 2008-02-05
Thanks, this clears one of my questions I was about to post!

---


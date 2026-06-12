---
title: "Ubuntu Server 12.04 LAN fails on reboot after auto upgrade (sometimes"
date: 2016-03-02
forum: Server Platforms
---

### Post by pharmswo on 2016-03-02
Hi,

I have an intermittent problem with my Ubuntu Server 12.04.
Auto upgrade is set for security upgrades.
Naturally sometimes after an autoupgrade a reboot is required. 

My problem is that sometimes after rebooting, manually from the command line, the LAN does not work. 

The only way of recovering this is a hard reboot.

Can anyone help with this?

07:24 reboot command was issued.
07:33 Hard reboot

It looks like the reboot fails to shut the system down.



Mar  2 07:24:39 server1 kernel: Kernel logging (proc) stopped.
Mar  2 07:24:39 server1 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="552" x-info="http://www.rsyslog.com"] exiting on signal 15.
Mar  2 07:33:25 server1 kernel: imklog 5.8.6, log source = /proc/kmsg started.

Regards

Paul

---

### Post by deadflowr on 2016-03-02
Moved to **Server Platforms**

---


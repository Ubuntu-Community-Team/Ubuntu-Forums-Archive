---
title: "Ubuntu 15.1 multipath breaks"
date: 2016-01-20
forum: Server Platforms
---

### Post by Igal_Katzir on 2016-01-20
Hello Ubuntu freaks,
I am having a problem with Ubuntu Server 15.1 installed as a VM.
The problem I encounter is with multipathing, I have dual path to the storage array and running a constant load test to check if it breaks during a path disconnection.
I am using the default settings and my mount point looks like this:
/dev/mapper/36742b0f00000047e000000000002238b    /iboxlun1    ext4    defaults    0    2

Problem Occurs whenever I disconnect a path, then return it back, and then disconnect the second path;
After few seconds the load test breaks and I see 'ugly' messages both on /var/log/syslog and dmesg.

Does anyone knows it this could be a Bug or a configuration issue?

thanks,
Igal

---

### Post by slickymaster on 2016-01-20
*Moved to the ***Server Platforms*** sub-forum*

---


---
title: "Ubuntu server 12.04 cannot connect"
date: 2016-06-23
forum: Server Platforms
---

### Post by fernandoch on 2016-06-23
Hello,

I have an Ubuntu 12.04 server with LAMP installed.

Recently I started getting that my http monitor is down.

I check the websites and they do not load.

I try to ssh the server and not possible.

I can just reboot the server via the console then everything gets back to normal.

How would be the best way to debug that?

Thanks

---

### Post by TheFu on 2016-06-23
What do the log files say?  If not much, you should turn up the logging to gain more information.  If the system hasn't been patched, it is likely to have been hacked.

---

### Post by fernandoch on 2016-06-23
What log file should I check?

---

### Post by TheFu on 2016-06-23
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by fernandoch on 2016-06-23
Yes, there are tons of log files.

---

### Post by TheFu on 2016-06-23
> **fernandoch said:**
> Yes, there are tons of log files.

And what do they say?  There is a story in those files. They probably tell what is happening on the system. 
Start by looking for warnings and errors.  I'd use grep/egrep to filter across all the files.

---


---
title: "Please help me understand how log files are managed."
date: 2009-10-21
forum: Server Platforms
---

### Post by chrismyers on 2009-10-21
Hi there,

/var/log contains lots of useful logs.

I can see that older logs appear to get gzipped.

My question is:

Do the logs continue to fill up disk space without expiring & being deleted?

Do I have to do this manually on the servers that I have built, or is there a system for cleaning out old logs?

Cheers,

Chris.

---

### Post by compiledkernel on 2009-10-21
[http://gwos.org/udsf/doku.php/hardware:diagnosis](http://gwos.org/udsf/doku.php/hardware:diagnosis)

Brief log explanation there. Generally speaking no, Logrotate is by default used to gzip logs (and delete them) based on age. 

For understanding logrotate read here -- 

[https://wiki.ubuntu.com/LinuxLogFiles](https://wiki.ubuntu.com/LinuxLogFiles)

---


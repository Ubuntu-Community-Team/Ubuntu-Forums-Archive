---
title: "What's your favorites Linux monitoring and management tool"
date: 2010-11-30
forum: Server Platforms
---

### Post by albertwt on 2010-11-30
Hi Everyone,

I'd like to know what's the most publicly installed or widely used Linux system performance monitoring software that is available and compatible with Ubuntu 64 bit ?

I've installed Nagios in place for availability report but for the monitoring performance of more than 10 it is impractical to open SSH console running top for each server.

what I'd like to monitor is:
1. Disk space issue.
2. resource hog.
3. failed root / sudo login attempt.

any kind of suggestion would be greatly appreciated.

Thanks.

---

### Post by James78 on 2010-11-30
[http://nagios.sourceforge.net/docs/2_0/distributed.html](http://nagios.sourceforge.net/docs/2_0/distributed.html)

---

### Post by albertwt on 2010-11-30
ok, who can I install this on my Ubuntu ? 

**apt-get install nagios**

Can I include this agent in my Linux VM as template ?

---

### Post by Damiox on 2010-11-30
conky  .  before that was ' system-monitor'  but its a hog .

---


---
title: "Server crashing"
date: 2009-10-31
forum: Server Platforms
---

### Post by RossImlach on 2009-10-31
I just recently upgraded my server to 9.10 (On the day it came out in fact), however it frequently crashes. I had a look at dmesg when it was on, so I thought I'd post a little excerpt of it below to see if anyone can help me.

```
[   17.619923] type=1505 audit(1257008316.275:13): operation="profile_replace" pid=766 name=/usr/sbin/tcpdump
[   21.032480] type=1503 audit(1257008319.691:14): operation="open" pid=996 parent=995 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.355451] type=1503 audit(1257008320.011:15): operation="open" pid=1016 parent=1015 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.652783] type=1503 audit(1257008322.132:16): operation="open" pid=1132 parent=1023 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.529190] type=1503 audit(1257008323.008:17): operation="open" pid=1148 parent=1147 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

```

And things like that repeat.  Is there anything else I should be looking for, or is this just a random occurrence? 

Thanks in advance..

---

### Post by Sporkman on 2009-10-31
It looks like apparmor is shutting down mysql for violating its profile restrictions... Did you explicitly enable this profile?

Is there a file called "usr.sbin.mysqld" under /etc/apparmor.d ?

---


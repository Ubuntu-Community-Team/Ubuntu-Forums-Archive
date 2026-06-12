---
title: "Today's updates to bind DNS -- permission denied?"
date: 2008-10-23
forum: Server Platforms
---

### Post by davidshere on 2008-10-23
This is "Solved", but I thought I'd share this in case someone else has the same problem, or if someone has some suggestions.  

I run three DNS servers with bind9 on Ubuntu Server 8.04.  Today I ran some updates.  At the end of the update process, bind was restarted, but failed:

```
Oct 23 08:17:02 raptor named[18495]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Oct 23 08:17:02 raptor named[18495]: found 1 CPU, using 1 worker thread
Oct 23 08:17:02 raptor named[18495]: loading configuration from '/etc/bind/named.conf'
Oct 23 08:17:02 raptor named[18495]: none:0: open: /etc/bind/named.conf: permission denied
Oct 23 08:17:02 raptor named[18495]: loading configuration: permission denied
Oct 23 08:17:02 raptor named[18495]: exiting (due to fatal error)
Oct 23 08:17:02 raptor kernel: [577470.268168] audit(1224764222.531:17): type=1503 operation="inode_permission" requested_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=18496 profile="/usr/sbin/named" namespace="default"
```

Without changing any settings, I reset two of the computers, and this problem went away on both of them.  (I have not yet reset the third one)

---


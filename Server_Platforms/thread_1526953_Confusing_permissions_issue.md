---
title: "Confusing permissions issue"
date: 2010-07-08
forum: Server Platforms
---

### Post by qwertybyrd on 2010-07-08
In setting up bind9 and dhcpd3-server, I have become confused about how permissions are working. After trying a number of things that should have worked but didn't, I finally ran across something that shouldn't have worked, but did:

**The background:**
in /etc/passwd: dhcpd:x:116:123::/var/run:/bin/bash
I read this as username dhcpd, uid = 116, and gid = 123.

in /etc/group: bind:x:123:
I read this as group bind is gid 123, and has no other members.
also:  - dhcpd:x:124:
group dhcpd is gid 124

ls -lh /etc/bind/rndc.key - 
-rw-rw---- 1 bind dhcpd 77 2010-07-06 13:29 /etc/bind/rndc.key

**What's happening:**
dhcp3-server works, and I don't understand why. The dhcpd user is NOT a member of the dhcpd group, so why can it open the file?

The converse of this is that if I set the group of rndc.key to bind - which the dhcpd user IS a member of, I get:
Can't open /etc/bind/rndc.key: Permission denied

So what am I missing, and why does just adding the dhcpd user to the bind group not work? ( where the default groups are normal and the ownership of rndc.key is bind:bind )

---


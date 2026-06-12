---
title: "tcpdump user privilage"
date: 2011-08-18
forum: Server Platforms
---

### Post by kaltsi on 2011-08-18
Hi,

I have a task to make tcpdump raw packet file from port of tcp 25.
I can do this, but only by root user. I would like do this by another user such as snoop. I use sudo command from noop user privilage and it's work fine. But how can I set the raw packet file privilage? The file privilage is always root.

snoop@admin:~$sudo tcpdump -i eth0 -w snoop.dump

---

### Post by iissmart on 2011-08-21
Set the suid bit on the permissions of tcpdump.

```
# which tcpdump | xargs chmod u+s
```

Something like that should work, run as root. Note that this means *any* user can use tcpdump now (generally not acceptable in the real world).

---


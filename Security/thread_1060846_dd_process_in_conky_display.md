---
title: "dd process in conky display"
date: 2009-02-05
forum: Security
---

### Post by chunchengch on 2009-02-05
I just find dd process in conky display, I don't understand why this process is running by itself, is it normal? thanks for reply.

[ATTACH]102244[/ATTACH]

---

### Post by jgoguen on 2009-02-07
It's probably fine.  Check the full path (in the terminal, using **ps -ef**, if you can't do that with conky) for both dd and klogd.  Here's how it looks for me:
```
root      4953     1  0 Feb06 ?        00:00:01 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4955     1  0 Feb06 ?        00:00:01 /sbin/klogd -P /var/run/klogd/kmsg
```
That means that klogd is using /var/run/klogd/kmsg as the source for kernel messages, and dd is writing messages from /proc/kmesg to /var/run/klogd/kmsg.  If that's how it looks (remember that pretty much everything between the usernames and the commands will probably be different for you), you're fine :)

---


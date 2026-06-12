---
title: "NFS mount hangs boot -- DNS unavailable"
date: 2010-06-17
forum: Server Platforms
---

### Post by cjstone on 2010-06-17
Hi, I posted this on Launchpad last week, but got no bites. Thought I'd try here as well..

This is on a freshly installed 10.04 server machine. /etc/fstab has this line:

```
netapp1.my.own.domain:/vol/vol2/repo_ubuntu /var/spool/apt-mirror nfs rw,rsize=8192,wsize=8192,hard,intr 0 0
```

When the machine is booted, mount -a has no problem mounting this export, however during boot, mountall attempts to mount it but reports it's unable to resolve the hostname of the export. The booting process hangs at this point.

Changing the hostname in the fstab to an IP resolves the issue, but I don't find that a satisfactory solution. Apparently, the resolvers listed in /etc/resolv.conf are not available to mountall at that point in the boot process. Networking does appear to be functional, however, as I can still ping the box while it's hung (and again, using the IP instead of the hostname allows the mount to occur).

resolvconf is not installed.

I'm still a bit new to the ubuntu startup process, but I'm looking into that now. Does anyone have any pointers?

Thanks,

--C

---


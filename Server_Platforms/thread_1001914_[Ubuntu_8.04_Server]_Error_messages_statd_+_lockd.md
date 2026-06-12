---
title: "[Ubuntu 8.04 Server] Error messages statd + lockd"
date: 2008-12-04
forum: Server Platforms
---

### Post by Peperzaken on 2008-12-04
Hello,

We have a Ubuntu 8.04 (file)server with OpenLDAP, NFS and Netatalk. Our clients are macs. NFS exports the homedirectory's for the LDAP users and the macs are configured to login on LDAP and uses the NFS homedirectory's. That works fine, but sometimes the macs freezes completely. In this case, the output of /var/log/syslog is:

```

Oct 24 09:43:00 asgard kernel: [3602712.339977] statd: server localhost not responding, timed out
Oct 24 09:43:00 asgard kernel: [3602712.340007] lockd: cannot monitor new-host-3.peperzaken.nl
```

I think this is the most relevant output in this log message. I searched at Google and found some information about this problem:

[http://www.linuxquestions.org/questions/linux-server-73/nfs-file-lock-issue-682810/](http://www.linuxquestions.org/questions/linux-server-73/nfs-file-lock-issue-682810/)
[http://wiki.skolelinux.de/Skolelinux/Ubuntu](http://wiki.skolelinux.de/Skolelinux/Ubuntu)

The "solution" was to (re)install nfs-common but this package was already installed. I found a topic on this forum about this problem, but it had no reply's, so it couldn't help me further.

Does anyone know how I can fix this? The kernel version is 2.6.24-19. NFS have the version number 1:1.1.2-2ubuntu2.

If I forgot some useful information, please let me know.

---

### Post by Peperzaken on 2008-12-05
Anyone?

---

### Post by Peperzaken on 2008-12-09
Kick

---


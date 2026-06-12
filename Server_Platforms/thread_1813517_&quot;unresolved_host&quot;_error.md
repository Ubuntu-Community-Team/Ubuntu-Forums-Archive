---
title: "&quot;unresolved host&quot; error"
date: 2011-07-27
forum: Server Platforms
---

### Post by SOMDdan on 2011-07-27
I have a dedicated box for my Ubuntu server. I have a shared directory ***/nethome, ***and it is listed in ***/etc/exports***. When I mount it from a Ubuntu laptop with "***mount -t nfs 192.168.102.40:/nethome/home/dan/Desktop/NH ***it mounts fine and is accessible. When I mount it from another Ubuntu machine, with the exact same command, I get the error message "unable to resolve host GATEWAY" (GATEWAY is my old Gateway laptop). The thing is I am not using DNS on my network. I did change the hostname previously with the ***hostname ***command, but I am not using hostnames to connect on the network. What does that error **really** mean?

---

### Post by volkswagner on 2011-07-27
Perhaps you previously created an entry in /etc/hosts on the computer throwing the error?

```
cat /etc/hosts
```

Do you see an entry with that ip address?  If so edit the file and change the hostname to match or comment out that line.

---

### Post by luwenliang0611 on 2011-07-28
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---


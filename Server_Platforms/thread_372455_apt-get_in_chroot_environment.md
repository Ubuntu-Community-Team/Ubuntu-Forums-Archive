---
title: "apt-get in chroot environment?"
date: 2007-02-28
forum: Server Platforms
---

### Post by Thoron on 2007-02-28
Hi,

we have an server here from which our 4 machines, where the user can log in with their terminals, grab their file systems via nfs.

No we would like to update to edgy. The problem is that we don't want to log in to one of the 4 machines and make the dist-upgrade because their file system is ro for security reasons.

We would like to chroot from the server to the directory and make the dist-upgrade.

The question is if thats possible and what kind of problems we might get? Does chroot prevent apt-get from messing around with the processes on the machine? We don't want to get any processes killed.

Thanks,

Martin

---


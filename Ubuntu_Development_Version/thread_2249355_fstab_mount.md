---
title: "fstab mount"
date: 2014-10-21
forum: Ubuntu Development Version
---

### Post by P-I H on 2014-10-21
In /etc/default/nfs-common you are able to define if systemd is used or not.
Default is like below, no value is set.
```
# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

```
I used systemd with the value set to "yes"
```
# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=yes

```
When I switched back to upstart I forgot this change and folders on my server wasn't mounted.
To get fstab mount to work again a had to set "no" as value.
```
# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=no

```

---

### Post by zika on 2014-10-21
As far as I do remeber it is not just SystemD issue with statd. You're writing about something that was a kind-of-a-bug already a while ago [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/305589](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/305589)

---


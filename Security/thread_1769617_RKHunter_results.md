---
title: "RKHunter results"
date: 2011-05-28
forum: Security
---

### Post by drakejacob on 2011-05-28
I have just installed rkhunter after reading a post and the results were

[17:40:57] Warning: Suspicious file types found in /dev:
[17:40:57]          /dev/shm/pulse-shm-2171343132: data
[17:40:57]          /dev/shm/pulse-shm-172501879: data
[17:40:57]          /dev/shm/pulse-shm-1340549872: data
[17:40:58]          /dev/shm/pulse-shm-2884315520: data
[17:40:58]          /dev/shm/pulse-shm-2706864647: data
[17:40:58]   Checking for hidden files and directories       [ Warning ]
[17:40:58] Warning: Hidden directory found: /etc/.java
[17:40:58] Warning: Hidden directory found: /dev/.udev
[17:40:58] Warning: Hidden directory found: /dev/.initramfs
[17:40:58] Warning: Hidden file found: /dev/.blkid.tab: ASCII text
[17:40:58] Warning: Hidden file found: /dev/.blkid.tab.old: ASCII text
[17:41:13]

Can anyone please tell me what this means?

---

### Post by CharlesA on 2011-05-28
rkhunter is known to give false positives.

It looks normal (with the usual false positives) to me.

---

### Post by drakejacob on 2011-05-28
> **CharlesA said:**
> rkhunter is known to give false positives.

It looks normal (with the usual false positives) to me.

Thank your for the help. So, it means that rkhunter is prone to give these false positives all the time.

---

### Post by CharlesA on 2011-05-28
> **drakejacob said:**
> Thank your for the help. So, it means that rkhunter is prone to give these false positives all the time.

Yes. If you so a search on this forum, you'll find quite a few threads about.

---


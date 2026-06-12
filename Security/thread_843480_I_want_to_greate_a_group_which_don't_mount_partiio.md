---
title: "I want to greate a group which don't mount partiions in /etc/fstab as they login....."
date: 2008-06-28
forum: Security
---

### Post by tttp on 2008-06-28
I want to create a group which don't mount partiions in /etc/fstab as they logging in....

When I create a new user, they log in to ubuntu desktop with mounted ntfs partitions in my computer as default. If I want to let some groups can't access the other partitoins in my pc, what should I do to achieve this goal?

---

### Post by Victormd on 2008-06-28
Check the link on my signature, there's a brief explanation on permission setting based on user groups...

---

### Post by tttp on 2008-06-29
> **Victormd said:**
> Check the link on my signature, there's a brief explanation on permission setting based on user groups...

Gid 46 means group plugdev, but I don't Know how to change the members of plugdev. In my /etc/group, plugdev group just only contain one member called haldaemon...and I can't find any members in group haldaemon because in /etc/group haldaemon only has such definition shown below:
==============================
haldaemon:x:116:
==============================

Even if  my new users are not in group haldaemon, they still can automount the partitions on my HD when they logging in this Desktop system. 

Maybe there is an access control list somewhere else to control who can mount all the partitions.....

---


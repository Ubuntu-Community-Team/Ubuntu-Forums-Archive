---
title: "KVM - Can’t Migrate from One Head"
date: 2018-11-12
forum: Virtualisation
---

### Post by jrajra on 2018-11-12
Hi all - anyone even use KVM on here? Have an odd one…


On one head, I can migrate guests to it, but can’t live migrate guests from it; have to pause them first. Error message appears saying either “Unable to migrate guest: internal error: owner -1 does not hold the resource lock” or complains it couldn’t lock a particular iscsi target; though the iscsi target it complains of (which sometimes changes) isn’t the one that belongs to that VM.


I’ve also spotted that the dm number (eg dm-12) in the multipath device enumerator doesn’t match the id of the device shown in multipath -ll across heads; eg 360014050cadca29d035dd3697d9e2ede will be dm-17 on one head, and 360014050cadca29d035dd3697d9e2ede is dm-6 on another. This is inconsistent across all heads.


Whelp?

---


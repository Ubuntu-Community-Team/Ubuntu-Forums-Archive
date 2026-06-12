---
title: "XFS and quota"
date: 2007-09-16
forum: Server Platforms
---

### Post by rinzwind80 on 2007-09-16
I'am stuck. I can't find the right information to enable quota on a XFS filesystem (for use with ISPConfig). Can anybody comment on this? Google doesn't help!

My partition scheme is basic: / and swap.

fstab options usrquota or quota and grpquota or gquota gives unknown mount option error message.
I've added rootflags=quota,gquota in lilo.conf. But not sure if that did it. Quota report commands give empty results (nothing printed)...

---


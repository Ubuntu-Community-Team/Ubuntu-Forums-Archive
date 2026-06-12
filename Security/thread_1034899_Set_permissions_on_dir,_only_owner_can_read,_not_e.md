---
title: "Set permissions on dir, only owner can read, not even root can."
date: 2009-01-09
forum: Security
---

### Post by kbah on 2009-01-09
(Using Gutsy, but solution on some release newer than it is welcome too)

Hi,

 I wanna know if it's possible to set permissions on a certain partition (ext3/reiserfs) and directory (by adding mount options to /etc/fstab) so that only the owner of that partition can read there, not even root can do it. I know that root can su do that user, etc.. but I wanna know if it's possible to do it.
 
 I guess I could let the partition on a remote computer, with no services running, just ssh, and accessible to only one user (AllowUsers user1), then, on the machine which has all the services I would mount that remote partition using sshfs, so I know only the user who mounted it would be able to read there, root on that machine (with the services running) would not be able to read on the directory. But this is just if I cannot find another better solution.
 I don't know if SELinux or some similar could give me that feature. Using these kind of kernel patches is too much, since you would spend lots of time configuring it, (correct me if I'm wrong).
 Finally, I don't know the status of AppArmor on Ubuntu. I'm used to run Suse, and don't know if AppArmor is well integrated with Ubuntu.

 thanks for your time.

---

### Post by hyper_ch on 2009-01-09
use encryption instead... root has access to everything.

---

### Post by The Cog on 2009-01-09
Root has access to all directories. And root will have access to encrypted directories of yours while the un-encrypted content is mounted (while you're logged in and using the directory yourself).

Think about it - root can always su to your id and then he will be you - permissions can't keep root out.

---


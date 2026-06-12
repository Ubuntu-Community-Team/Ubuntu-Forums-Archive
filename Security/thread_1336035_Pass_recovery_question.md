---
title: "Pass recovery question"
date: 2009-11-24
forum: Security
---

### Post by laimonas on 2009-11-24
Hi there,

I don't know if there was similar question or not. If there was, then add link :)
Ok the problem: I think most of you know how to recovery password from boot menu. The situation - other person, who sit down near my computer and who try to login, know my login name. Then he could change my pass with recovery menu. And how to do that he couldn't change pass? Maybe somehow I can modify recovery menu and disable pass recovery function?

---

### Post by Logan1985 on 2009-11-24
> **laimonas said:**
> Hi there,

I don't know if there was similar question or not. If there was, then add link :)
Ok the problem: I think most of you know how to recovery password from boot menu. The situation - other person, who sit down near my computer and who try to login, know my login name. Then he could change my pass with recovery menu. And how to do that he couldn't change pass? Maybe somehow I can modify recovery menu and disable pass recovery function?

What you can do is secure GRUB - The boot loader

Take a look at the tutorial here - [http://ubuntuforums.org/showthread.php?t=715630](http://ubuntuforums.org/showthread.php?t=715630) (I am not entirely sure if this applies verbatim to 9.10 mind. You will need to check specific file paths)

However, this doesn't then mean that you are totally safe - if you are really concerned about this then you may wish to consider full disk encryption because even with GRUB secured someone could use a live CD to mount your file system, and then just set your password to blank.

---

### Post by laimonas on 2009-11-24
Thanks man, It was helpful. And I was thinking about the permission of all files with live cd. I've got the answer about that too. Thanks again :)

---

### Post by cdenley on 2009-11-24
Physical access means they can read/alter any files on an unencrypted filesystem one way or another. The only real protection you have from physical access is encryption. If /etc is on an encrypted filesystem, then password hashes can't be reset until the filesystem is decrypted. Of course, they can always erase your encrypted filesystem, but they can't reset passwords.

---


---
title: "Urgent help"
date: 2014-09-25
forum: Server Platforms
---

### Post by gregor9 on 2014-09-25
Can someone help me with this!
[http://ubuntuforums.org/showthread.php?t=2245571](http://ubuntuforums.org/showthread.php?t=2245571)

---

### Post by T.J. on 2014-09-25
Forgive me if this sounds condescending (I assure you it is not), but  I do not know your personal level of skill.  Are you using the 64 bit or 32 bit version, as it may make a difference?

In the absence of knowing. according to the screen you have a damaged or missing file libudev.so, which is part of the hardware device layer.  You will need to boot the system with a recovery disk and repair the file in order for the system to boot properly.  If you feel confident that you will not lose anything critical, I would simply reinstall the OS, as this would be the least painful way to recover.    The safest method would be to use the recovery install disk to boot the system, put it into live mode (boot the Ubuntu CD but do not install), mount the drives manually and then backup your data. After you have saved your data, re-install the system, but this time do not leave it unattended.  

While best effort is made to make sure Ubuntu works, it is nonetheless a derived copy of Debian Testing or Debian Unstable, both of which can have serious bugs that go unfixed.  You should never trust Ubuntu to cleanly upgrade in place on an existing install.  In my personal opinion, Ubuntu should never be used on critical production systems.

If you want to try to recover without a reinstall, please let me know, and I will see what I can do to help you.

---

### Post by lisati on 2014-09-25
> **gregor9 said:**
> Can someone help me with this!
[http://ubuntuforums.org/showthread.php?t=2245571](http://ubuntuforums.org/showthread.php?t=2245571)

Having multiple threads about a problem can get confusing. BUMPing[*] an exisiting thread if you haven't had a reply for a while is usually better than starting a new thread.

Thread closed.

[*]BUMP = "Bring Up My Post"

---


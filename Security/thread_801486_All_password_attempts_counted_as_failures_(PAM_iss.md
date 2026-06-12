---
title: "All password attempts counted as failures (PAM issue...)"
date: 2008-05-20
forum: Security
---

### Post by khughitt on 2008-05-20
Hi all,

I recently set-up a machine with Ubuntu 8.04, and have run into some problems with getting pam settings to work properly. For my system, I need
to have it so that the user becomes locked out after three successive failed login attempts, and that the computer is locked whenever the screensaver (gnome-screensaver) starts up.

This I have managed to get. The problem, however, is that now ALL login/sudo attempts are counted as failed attempts, even if they work properly, and once this reaches the limit (3), I become locked out.

For example, suppose I run **faillog**, and it shows "1" under failures next to my username. next I execute some command using sudo, e.g. "sudo -l." The command works properly, however, when I run faillog again it shows I now have two failures. If I try again, after the next sudo command, my account becomes locked and it will start failing ("Sorry, try again."), If I break when asked to enter a password it says "pam_authenticate: Conversation error."

Anyone know what is going on? Any suggestions would be greatly appreciated.

Thanks!

---

### Post by khughitt on 2008-05-27
Okay,

Still no luck. I reverted to the default PAM settings, and things are working fine now, however, I would still like to get it working so that I can lock accounts after a number of failed logins.

Anyone have any ideas?


Thanks,

---


---
title: "[Ubuntu] Login timed out when trying to login at reboot"
date: 2010-07-13
forum: Server Platforms
---

### Post by timothy_tim on 2010-07-13
I'm hosting a server with Ubuntu 10.04. I've stumbled upon a strange problem.
The server seems to refuse any login attempts, either with SSH or via a TTY after a reboot. After a couple of minutes (about 10 minutes or so) I able to login. The memory usage isn't high at login nor the system load. The auth.log doesn't show any login attempt before.

Does anybody else have this problem? Or does anybody have a suggestion I could try to fix this?

---

### Post by timothy_tim on 2010-07-13
I seem to have found the problem, winbindd is causing the problems.
When I kill the winbindd process everything works fine.

Anyone a suggestion?

---

### Post by ldpaniak on 2010-08-25
I see this too in Lucid x64 server after an upgrade from Karmic.

Reinstalling winbind does not help.

---


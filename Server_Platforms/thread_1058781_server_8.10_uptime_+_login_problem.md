---
title: "server 8.10 uptime + login problem"
date: 2009-02-03
forum: Server Platforms
---

### Post by blakew on 2009-02-03
Hi all,

this is probably just another thread to get lost in the myriad of threads that appear, but I've been having a problem with my ubuntu server box. It manages to run nicely for about a week (can't be specific, as i don't keep track), but then if I try to login to it, it gets up to entering my password, then once I do that, it does nothing (via ssh, presumably times out), and if I try logging in locally it eventually says "login timed out" after I enter my password.

Also, around the same time, I've noticed the kernel starts throwing my vuurmuur rules out of the tty1 console (coincidence?). Pressing ctrl+alt+delete makes some processes exit, however it stops dead in its tracks, and the kernel continues throwing up vuurmuur messages. pressing ctrl+alt+delete again has no effect, regardless of how many times it's pressed.

Would appreciate advice as to what to do. Can post any logs if needed, however I've spent half an hour looking at dmesg, syslog, auth.log, messages, daemon.log, as well as all of vuurmuur's logs, and none seem to give any hint as to the problem. Perhaps I've discovered some rare bug?

Oh, I should also mention that everything's fine upon reboot.

---


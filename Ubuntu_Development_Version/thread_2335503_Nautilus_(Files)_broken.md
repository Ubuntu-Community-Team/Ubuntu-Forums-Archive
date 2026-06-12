---
title: "Nautilus (Files) broken?"
date: 2016-08-29
forum: Ubuntu Development Version
---

### Post by sgage on 2016-08-29
I made a fresh install of the latest build, and when I try to run 'Files', the window comes up for a second or two and then disappears. Launching from the command line yields:

```
*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug

Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
**
ERROR:nautilus-canvas-container.c:6021:finish_adding_new_icons: assertion failed: (!container->details->auto_layout)
Aborted (core dumped)

```

Anyone know what's going on?

---

### Post by sgage on 2016-08-29
Solved. Some nautilus-related updates came in, but the problem persisted. I deleted .config/nautilus and .local/share/nautilus, and all seems to be working fine now.

---

### Post by bixejo on 2017-02-26
> **sgage said:**
> Solved. Some nautilus-related updates came in, but the problem persisted. I deleted .config/nautilus and .local/share/nautilus, and all seems to be working fine now.

Thank you!

This workaround worked for me fine too.

---

### Post by lucas7bm on 2017-05-16
Just installed Ubuntu Budgie and had this problem.
This workaround just nailed it too. Thank you!

---

### Post by jbicha on 2017-05-16
If anyone else experiences this bug, it would be move useful to move those files and folders somewhere else instead of deleting them. That way, you can file a bug with those attached so someone can figure out what's causing upgrades to not work.

---


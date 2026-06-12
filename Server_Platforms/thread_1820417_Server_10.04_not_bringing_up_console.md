---
title: "Server 10.04 not bringing up console"
date: 2011-08-07
forum: Server Platforms
---

### Post by Kainwolf on 2011-08-07
I'm having an issue with Ubuntu 10.04 server, where it is not bringing up a console on the local machine.

The only display on the local screen (and in /var/log/boot.log) is:
```
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 100725/2342912 files, 781590/9357824 blocks
init: ureadahead-other main process (595) terminated with status 4
```

Hitting <alt>-<f[anything]> just brings up a blank screen with a single flashing cursor, and no login prompt.

The ureadahead message sounds like the classic Windows error:  "The operation could not be completed because of the following error: The operation completed successfully." So ureadahead isn't the problem.

Also... ssh works, but other services (apache, mysql, smbd, nfs-kernel-server, etc) need to be started manually.

Any thoughts?

---

### Post by volkswagner on 2011-08-07
Is this a fresh install?

Check out [this]("http://ubuntuforums.org/showthread.php?t=1484694") thread.

For my similar problem after fresh install, find [solution post]("http://ubuntuforums.org/showpost.php?p=10906698&postcount=22"), in above thread.

---

### Post by Kainwolf on 2011-08-07
Thanks for the tip and thread.
Sorry no that didn't help.
It's not a new install either.

Still I've gone in and altered /etc/default/grub to:
```
...
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
...
```

Same situation; I'd even enabled the next parameter prior to this, but that didn't resolve...
GRUB_GFXMODE=640x480

(and I ran update-grub after each change before restarting).

---


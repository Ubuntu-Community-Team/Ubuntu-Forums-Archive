---
title: "Stops at loading initial ramdisk"
date: 2017-04-16
forum: Server Platforms
---

### Post by jonnier on 2017-04-16
Hi,

So this morning I updated my 16.04.2 server installation, and can now only get to a normal state by booting through recovery.

I've added nomodeset to the grub config, although I'm using an AMD ATI card in case I need to connect monitor.  One thing that seems odd is that despite changing the timeout settings in /etc/default/grub the grub menu always waits 30 seconds.  I've run update-grub just to be sure, but it still makes no difference when booting.  The only other grub options are acpi=off and apm=off.

I believe the problem has occurred because I stupidly selected the option to allow the package maintainers grub config to overwrite my existing grub config.


Jon

---


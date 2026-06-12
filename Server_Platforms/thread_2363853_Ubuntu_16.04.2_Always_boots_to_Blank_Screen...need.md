---
title: "Ubuntu 16.04.2 Always boots to Blank Screen...need to press Alt-F7"
date: 2017-06-15
forum: Server Platforms
---

### Post by hitechcompliance on 2017-06-15
Hi
My Ubuntu LUKS 16.07.2 Server always boots to a Blank Screen and need to Press Alt-F1 then Alt-F7 to get to the pass prompt.
Rather annoying.
Contents of my grub file
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=" net.ifnames=0 biosdevname=0 splash"
GRUB_CMDLINE_LINUX=""

Everything else is commented out.

Thanks

---

### Post by howefield on 2017-06-15
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by cariboo on 2017-06-15
Might this be causing the problem?

```
GRUB_CMDLINE_LINUX_DEFAULT=" net.ifnames=0 biosdevname=0 splash"
```

on my server the line looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

---


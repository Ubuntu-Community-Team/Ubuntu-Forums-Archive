---
title: "How to turn my USB passport drive off on Ubuntu headless server"
date: 2011-07-29
forum: Server Platforms
---

### Post by jocampo on 2011-07-29
This is a silly question maybe, but how can I turn my passport drive off after has being unmounted? I am assuming that's the right order, before removing: umount and then turning off.

By the way, I am talking about Ubuntu Server, not regular Ubuntu desktop via GUI.

---

### Post by papibe on 2011-07-29
AFAIK, it is a USB powered HD, so once it has been unmounted, you have to unplug it to turn it off.

Depending on the power saving settings of the drive itself, it could turn itself off (or at least into power savings mode) just by unmounting it.

Just some thoughts,
Regards.

---

### Post by jocampo on 2011-07-29
Thanks for reply.

Well ... the external drive is USB port powered but does not turn itself off after umount. It does though if I use it on Ubuntu desktop and select safely remove.

On Ubuntu Server, it does not turn power off after umount. Is that normal, will that cause data corruption or disk issues over the time?

---


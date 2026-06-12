---
title: "Gutsy as guest cannot read music CD's in VB"
date: 2007-11-15
forum: Virtualisation
---

### Post by jaezcurra on 2007-11-15
Having Gutsy as guest in a WXP host with VirtualBox 1.5.2 I cannot play music CD's: I get an error message ("Cannot mount volume. Invalid mount option when attempting to mount the volume").
Data CD's work 100% OK.

---

### Post by hidannik on 2010-01-03
As of version 3.1.2, VirtualBox does not support audio CDs.  From section 5.7 of the user manual:[INDENT]In any case, only data media is supported for CD/DVD drives. This means that all data CD formats and all DVD formats can be used in principle. Since host DVD drives refuse to read encrypted DVD video media, you cannot play such videos with the regular CD/DVD drive emulation. You may be able to get it working with the experimental passthrough support described in Section 5.8, “Writing CDs and DVDs using the host drive”. **Audio CD and video CD formats are not supported, which means you cannot play such media from a virtual machine.** [emphasis mine]
[/INDENT]I suggest using VMWare Server (1.0.x) instead, it has pretty good support for this stuff. Unfortunately, its performance is slower, and Windows guests crash when USB 2.0 devices are plugged in, unless you turn off USB 2.0 support in your BIOS.

Hans Dannik

---

### Post by jaezcurra on 2010-01-18
Thank you for the reply.  Currently I am dualbooting, so I have no those virtualization needs ;)

---


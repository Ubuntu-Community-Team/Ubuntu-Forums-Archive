---
title: "Problem with Boot of System76 Pangolin V3/4 - Seems USB related"
date: 2010-06-28
forum: System76 Support
---

### Post by gbutler69 on 2010-06-28
I'm having the same problem as posted about here: [http://wwww.ubuntuforums.org/showthread.php?t=621362](http://wwww.ubuntuforums.org/showthread.php?t=621362). In it it was said the boot was hanging after/during the BIOS Post and then you were getting messages like:

    Jun 28 20:36:54 gbutler-laptop kernel: [   95.240097] hub 1-0:1.0: connect-debounce failed, port 2 disabled
    Jun 28 20:36:56 gbutler-laptop kernel: [   97.832511] hub 1-0:1.0: connect-debounce failed, port 2 disabled
    Jun 28 20:36:59 gbutler-laptop kernel: [  100.280086] hub 1-0:1.0: connect-debounce failed, port 2 disabled
    Jun 28 20:37:01 gbutler-laptop kernel: [  102.701900] hub 1-0:1.0: connect-debounce failed, port 2 disabled
    Jun 28 20:37:04 gbutler-laptop kernel: [  105.140076] hub 1-0:1.0: connect-debounce failed, port 2 disabled

I too am experiencing this issue. It seems hardware related. I now need to let BIOS Post begin, let it hang, then press CTRL-ALT-DEL (during the hung BIOS Post before it loads GRUB as far as I can tell) and then let it re-boot. After the Re-Boot, sometime I get the above messages in the kern.log, sometimes I don't. Regardless, It doesn't boot smoothly. This came on all of the sudden out of nowhere. Did you ever figure it out? (I'm on a System75 Pangolin Performance V3/4 purchased September 2009 - this is my third System76 Laptop). Any information you might have would be greatly appreciated.

Thanks in Advance.

---

### Post by gbutler69 on 2010-06-29
Is this support forum for System76 still alive?

---

### Post by isantop on 2010-06-29
Yes, we still check it every day. We're looking in to your issue.

You said it might be USB related. Does having a USB device in a USB port make a difference in whether the system boots cleanly or not?

---

### Post by gbutler69 on 2010-06-29
No, having a USB device connected or not does not seem to change anything. It just gets stuck during the boot process (before GRUB and the Linux Kernel as far as I can tell, during the BIOS POST etc). My saying it might be USB related goes on the nature of the messages the Kernel is producing after I hit CTRL-ALT-DEL and let it Re-Boot (and it gets past the BIOS Boot-Up process). It seems like somehow the BIOS is getting stuck initializing the USB HUB or somesuch. Then, it seems like the CTRL-ALT-DEL causes the BIOS to skip needing to initialize the USB hub. Then Kernel tries to initialize and/or communicate with it and gets the errors I showed. I don't seem to see any problem with USB though. It seems like all my USB ports (3 of them) work correctly.

Anything I could try to confirm if this is a hardware issue or not?

---

### Post by isantop on 2010-06-29
Try opening the back panel of your computer and reseating the memory.

---

### Post by gbutler69 on 2010-06-29
I'll give that a try and report back. Thanks.

---


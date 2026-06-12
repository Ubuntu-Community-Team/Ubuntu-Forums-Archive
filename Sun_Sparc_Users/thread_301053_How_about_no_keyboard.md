---
title: "How about no keyboard?"
date: 2006-11-16
forum: Sun Sparc Users
---

### Post by mahy on 2006-11-16
Hello,

my Ultra 5 refuses to boot without a keyboard plugged in. I guess this is normal behavior, but it's undesirable in my case. I wanna log via SSH and VNC only. Can i somehow change it's mind to make it work without a keyboard? THX

---

### Post by Jussi Kukkonen on 2006-11-16
Check the BIOS settings. Should be there.

---

### Post by mahy on 2006-11-16
> **Jussi Kukkonen said:**
> Check the BIOS settings. Should be there.

eh? there's no BIOS in SPARC computers!

---

### Post by Jussi Kukkonen on 2006-11-16
Well, I guess so (I've never really understood that). I just meant to say that the refusal to boot probably happens before Linux, in whatever-the-bootloader-is-called (Open Boot Loader or something?).


EDIT: ...or so I thought. Decided to check after all, and it seems that gettys are the problem: [http://www.ultralinux.org/faq.html#q_6_13](http://www.ultralinux.org/faq.html#q_6_13)

---

### Post by Delta_Farce on 2006-11-16
Hi,

There's some information about booting Sun machines without a keyboard [here.]("http://mailgate.supereva.com/linux/linux.debian.ports.sparc/msg17292.html") It seems it is possible by either linking a null-modem cable to the machine or, in some cases, by just removing the keyboard.

Anyway, have a look at the Sun OBP Reference Card [here.]("http://www.unixzone.dk/unix/sun/resources/SunOBP_Quick_Ref.pdf") This should tell you how to switch input/output to a serial port (null modem). 

Hope this helps,

Mark

---


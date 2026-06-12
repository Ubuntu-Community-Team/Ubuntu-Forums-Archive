---
title: "Large File Transfers - Crash"
date: 2010-04-25
forum: Server Platforms
---

### Post by computerwiz_222 on 2010-04-25
Hello,

I have been running a Ubuntu server now for almost a year. This weekend I have decided to upgrade my Athlon 1700+ to a Pentium 4 3.0GHz HyperThreading. The system has two 1TB raid 1 and a gigabit lan card.

The system before the CPU upgrade could get up to 22 - 23 mb/s on a file transfer. After I upgraded the motherboard and CPU, I can get up to 40 mb/s but the system crashes after a few seconds of copying at this speed.

Any suggestions?

Thanks in advance!

---

### Post by KiLaHuRtZ on 2010-04-27
From my experience and in my opinion, a mobo swap/upgrade is a BIG change to the system and I would recommend you re-install.

---

### Post by uberlinuxnerd on 2010-04-27
> **KiLaHuRtZ said:**
> From my experience and in my opinion, a mobo swap/upgrade is a BIG change to the system and I would recommend you re-install.

If your using the default kernel this shouldn't be necessary, Big hardware changes needing a re-install is a *windowsisum *

OP is there any output in your system log when the transfer crashes? I would suspect a bad driver.

---

### Post by computerwiz_222 on 2010-04-27
Thanks for the speedy replies. I have been diagnosing it lately and it seems like I had a bad stick of ram in there. I pulled them out individually and tested them. I can now easily get 55mb/s transferring from my iMac to the Ubuntu server.

I didn't think I had to reinstall, that windows comment makes pretty good sense to me. 

Thanks for your help.

---

### Post by uberlinuxnerd on 2010-04-27
> **computerwiz_222 said:**
> Thanks for the speedy replies. I have been diagnosing it lately and it seems like I had a bad stick of ram in there. I pulled them out individually and tested them. I can now easily get 55mb/s transferring from my iMac to the Ubuntu server.

I didn't think I had to reinstall, that windows comment makes pretty good sense to me. 

Thanks for your help.

No problems! :P

---


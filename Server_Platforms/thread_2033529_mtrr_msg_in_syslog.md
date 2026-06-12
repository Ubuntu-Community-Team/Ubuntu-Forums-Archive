---
title: "mtrr msg in syslog"
date: 2012-07-26
forum: Server Platforms
---

### Post by btanseco on 2012-07-26
Hello Everybody,
Quick question when you get a chance.
We have Ubunt10 10.10 installed in one of our servers.
We see this error that occurs every 20sec.
We don't see any issues on the server yet but we want to know before something happens.  is there other places I can check that can give us a clue on what's going on?

Thank you for your future help,
btanseco

Jul 26 11:18:18 db1 kernel: [31838579.537135] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:18 db1 kernel: [31838579.537176] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:18 db1 kernel: [31838579.537211] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644226] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644267] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644302] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665570] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665610] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665645] mtrr: your BIOS has configured an incorrect mask, fixing it.

---

### Post by codemaniac on 2012-07-26
> **btanseco said:**
> Hello Everybody,
Quick question when you get a chance.
We have Ubunt10 10.10 installed in one of our servers.
We see this error that occurs every 20sec.
We don't see any issues on the server yet but we want to know before something happens.  is there other places I can check that can give us a clue on what's going on?

Thank you for your future help,
btanseco

Jul 26 11:18:18 db1 kernel: [31838579.537135] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:18 db1 kernel: [31838579.537176] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:18 db1 kernel: [31838579.537211] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644226] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644267] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:38 db1 kernel: [31838598.644302] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665570] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665610] mtrr: your BIOS has configured an incorrect mask, fixing it.
Jul 26 11:18:58 db1 kernel: [31838618.665645] mtrr: your BIOS has configured an incorrect mask, fixing it.

As you have already mentioned you are using an older version of Ubuntu , you might consider upgrading it to newer one .
However this type of incident has already been reported on launchpad for Lucid .

Please read the comments that might help you to fix this issue .
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568441](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568441)

---


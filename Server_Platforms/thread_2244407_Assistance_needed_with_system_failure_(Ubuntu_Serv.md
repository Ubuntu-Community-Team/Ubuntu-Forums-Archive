---
title: "Assistance needed with system failure (Ubuntu Server 14.04.1)"
date: 2014-09-16
forum: Server Platforms
---

### Post by ajgwilson on 2014-09-16
I'm running an Ubuntu Server 14.04 (3.13.0-35-generic) as a storage server. This morning I had to reset the system and the syslog possibly suggests a bug. I am not sufficiently knowledgeable to be able to interpret whether this is a kernel bug, module issue or hardware problem and would really appreciate some guidance! A section of the log is at:

[http://pastebin.com/YsEqH7Mp](http://pastebin.com/YsEqH7Mp)

---

### Post by konsole on 2014-09-22
Ensure that the Supermicro motherboard is running the latest bios.
Does the kernel oops occur using a previous kernel?
Try a mainline kernel and headers [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.2-utopic](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.2-utopic)
If all fails, work through this process: [https://wiki.ubuntu.com/DebuggingKernelOops](https://wiki.ubuntu.com/DebuggingKernelOops)
Good Luck.

---

### Post by Michael_McKenney on 2014-09-22
I had a server board from Supermicro with a pair of E5430s on it.  The bios was so flaky with Windows that I scrapped the board. I bought three bios chips for $25 each because flashing it would crash it.  Unless Supermicro fully supports the OS on their web site, I would get a new board.  Supermicro's policy is run only the OS they support.  Does the BIOS have switches for Linux?

---


---
title: "rcN.d links disappearing"
date: 2010-06-22
forum: Server Platforms
---

### Post by msobkow on 2010-06-22
We run Ubuntu 10.04 Server for our solutions, but I'm having a bizarre problem with init.d boot scripts.  I have a script for the Sangoma wanpipe drivers that I modified to add the LSB information so that "update rc.d wanrouter defaults" runs correctly.  The symbolic links from rcN.d to init.d get created appropriately.

However, when I reboot the system, all the rcN.d links have disappeared and wanrouter isn't automatically started!

I've never seen this kind of behaviour from a Unix based system in 20+ years, so I'm baffled as to how to fix the problem.

---

### Post by capscrew on 2010-06-22
> **msobkow said:**
> We run Ubuntu 10.04 Server for our solutions, but I'm having a bizarre problem with init.d boot scripts.  I have a script for the Sangoma wanpipe drivers that I modified to add the LSB information so that "update rc.d wanrouter defaults" runs correctly.  The symbolic links from rcN.d to init.d get created appropriately.

However, when I reboot the system, all the rcN.d links have disappeared and wanrouter isn't automatically started!

I've never seen this kind of behaviour from a Unix based system in 20+ years, so I'm baffled as to how to fix the problem.

As of 10.04 Ubuntu is now using Upstart instead of init scripts for most things.  See [**_here _**]("http://www.linux.com/archive/feature/125977") for some information.

---


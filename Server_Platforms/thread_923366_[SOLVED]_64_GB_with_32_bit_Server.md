---
title: "[SOLVED] 64 GB with 32 bit Server???"
date: 2008-09-18
forum: Server Platforms
---

### Post by Krupski on 2008-09-18
Hi,

I just saw this on the Ubuntu website:

**"For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB."**

Does this mean that the 32 bit version of Server, running on an Intel Core 2 Duo or Quad will use PAE and have up to 64 GB address space available to it?

If so, then why is there a 64 bit AMD/EMT64 version?

:confused:

---

### Post by Heinzelotto on 2008-09-18
PAE virtualizes the memory, direct access is faster, but only available to the 64-bit versions

---

### Post by Robstarusa on 2008-09-18
> **Krupski said:**
> Hi,

I just saw this on the Ubuntu website:

**"For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB."**

Does this mean that the 32 bit version of Server, running on an Intel Core 2 Duo or Quad will use PAE and have up to 64 GB address space available to it?

If so, then why is there a 64 bit AMD/EMT64 version?

:confused:

Even with PAE, individual processes still cannot use more than 4GB (someone correct me if I'm wrong).  PAE allows you to have 4GB (max) pages that can be given to processess.

64-bit allows any process to have > 4GB.

Also, from what I've read some device drivers do not play well with 32-bit/PAE.

---

### Post by Krupski on 2008-09-18
> **Heinzelotto said:**
> PAE virtualizes the memory, direct access is faster, but only available to the 64-bit versions

I know what PAE does hardware-wise. It's an extra 4 bits of address bus that can be used to select 16 4GB (32 bit) pages of ram, giving a virtual address space of 64 GB max (like EMM386 of days gone by).

My question is, if my file server box has an Intel Core 2 Duo processor (which supports "EMT64" and "PAE"), and I have 8 GB of ram installed, should I be using the 32 bit version of Server, or the 64 bit version (and why?).

Thanks!

-- Roger

---

### Post by Heinzelotto on 2008-09-18
use the 64-bit version since the extra addressable memory is not the only advantage of 64-bit (read more on wikipedia). On a server you also probably don't want to run flashplayer, which is the only program (which comes to my mind) that doesn't play well with 64-bit versions of linux

---

### Post by Krupski on 2008-09-18
> **Heinzelotto said:**
> use the 64-bit version since the extra addressable memory is not the only advantage of 64-bit (read more on wikipedia). On a server you also probably don't want to run flashplayer, which is the only program (which comes to my mind) that doesn't play well with 64-bit versions of linux

I won't be running the flash player or much of anything else as the machine I'm talking about is a file server.

I currently run the box with 64 bit Ubuntu Server... I just wondered about the thing I read about 32 bit vs. 64 bit and wanted to know.

Thanks!

-- Roger

---


---
title: "PHP Memory"
date: 2006-07-18
forum: Server Platforms
---

### Post by Ryan H on 2006-07-18
On my local server, which is running Ubuntu Linux 6.06 64-bit, when I run eigher my XML Parser, or others, such as the IPB parser, this error returns:
> 
**Fatal error:**  Allowed memory size of 8388608 bytes exhausted (tried to allocate 71 bytes)


It doesn't make sense because I know it's not using 8 MB of data, and I'm looking at system monitors as I do this and there is no significant change in memory. PHP isn't leaking memory so it must just not be properly examining memory sizes. Anyone have any ideas?

-Ryan

---


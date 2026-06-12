---
title: "Archiving &amp; Data Integrity"
date: 2010-04-20
forum: The Cafe
---

### Post by Sporkman on 2010-04-20
Hi All-

I just found a very neat tool: **par2** . Given a large file or set of files, it will construct a set of verification files that the tool can use at a later date to verify the integrity of the file(s) at a later date, and if any of the data was corrupted it will repair the data (up to a certain user-settable redundancy level). It does this using the fancy Reed-Solomon encoding scheme.

I figured I'd use that in any long-term archival process.

However I'm wondering if the new BRTFS filesystem would do that sort of thing automatically. I'd probably like to use both. :)

---

### Post by undecim on 2010-04-20
Yeah, par2 is pretty great. Especially when not all the files from a Usenet download are available, you can use the par files to reconstruct the missing files.

---


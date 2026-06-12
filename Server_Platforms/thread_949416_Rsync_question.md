---
title: "Rsync question"
date: 2008-10-16
forum: Server Platforms
---

### Post by stonneway on 2008-10-16
Hi,

Just a quicky. By Default does Rsync do differential copying? That is, if i run Rysnc once to copy a folder from one pc to another, then run the same command line again, will it copy all the files again or will it just copy any files that have changed ?

S

---

### Post by hyper_ch on 2008-10-16
it will just copy the parts of the files that were changed... or maybe the whole files that were changed... but it will not copy anything that was not changed.

---

### Post by lykwydchykyn on 2008-10-16
by default it copies whole files that have changed, but there is a switch to make it only copy the changes to the files.

---

### Post by MJN on 2008-10-16
> **lykwydchykyn said:**
> by default it copies whole files that have changed, but there is a switch to make it only copy the changes to the files.That's only if both the source and destination paths are local. If one isn't then the default is to use delta-transfer.

..but this is getting away from the OP's question so we should stop here for fear of confusing them further!

Mathew

---


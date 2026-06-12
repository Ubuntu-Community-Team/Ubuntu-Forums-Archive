---
title: "Knight's Ferry"
date: 2011-11-19
forum: The Cafe
---

### Post by An Sanct on 2011-11-19
Well, if you know what it is, then maybe you can answer the question I have (as it is hardly a support question, it is placed in the community cafe)

*If* I *somehow* got my hands on one of those things (32-Core), would it work with Ubuntu? Or would it be just a 300W energy eater without support?

[http://newsroom.intel.com/docs/DOC-2152/diff?secondVersionNumber=18](http://newsroom.intel.com/docs/DOC-2152/diff?secondVersionNumber=18)

---

### Post by Thewhistlingwind on 2011-11-19
> **An Sanct said:**
> Well, if you know what it is, then maybe you can answer the question I have (as it is hardly a support question, it is placed in the community cafe)

*If* I *somehow* got my hands on one of those things (32-Core), would it work with Ubuntu? Or would it be just a 300W energy eater without support?

[http://newsroom.intel.com/docs/DOC-2152/diff?secondVersionNumber=18](http://newsroom.intel.com/docs/DOC-2152/diff?secondVersionNumber=18)

A supercomputer that doesn't support Linux (90%> market share.) is poor indeed.

---

### Post by An Sanct on 2011-11-19
Well, it was kind of mind boggling to me too, to see windows 7 running on the test machine ... that is why I ask...

---

### Post by KiraLexi on 2011-11-20
Pretty sure it'll have programming support for both Windows and Linux.

Remember, it's not really a general-purpose CPU - it's a PCIe co-processor card, like a Tesla or a GRAPE-DR or any number of others. All it needs is drivers and compiler infrastructure (presumably a tweaked ICC with support for the wide vector units.)

Thewhistlingwind: a lot of supercomputers don't run much of an OS at all on the individual compute nodes. BlueGene, the Cray XMT, the Cray X2, etc all run ultra-minimal OS's on the compute nodes and use Linux for I/O (if at all.)

---


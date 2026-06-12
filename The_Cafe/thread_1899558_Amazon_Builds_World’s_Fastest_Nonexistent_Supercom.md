---
title: "Amazon Builds World’s Fastest Nonexistent Supercomputer"
date: 2011-12-23
forum: The Cafe
---

### Post by fdrake on 2011-12-23
from : [http://www.wired.com/wiredenterprise/2011/12/nonexistent-supercomputer/2/](http://www.wired.com/wiredenterprise/2011/12/nonexistent-supercomputer/2/)

> 
The 42nd fastest supercomputer on earth doesn’t exist.

This fall, Amazon built a virtual supercomputer atop its Elastic Compute Cloud — a web service that spins up virtual servers whenever you want them — and this nonexistent mega-machine outraced all but 41 of the world’s real supercomputers.



just wanted to hear your thoughts about this article and the future/benefits of virtual server in general.

---

### Post by 3Miro on 2011-12-23
Supercomputers are useful for scientific applications, however, an Internet based supercomputer has very limited use. The biggest drawback in supercomputing is the high cost of communication between the machines, that is on a local 2x1Gb network. On the Internet, unless your algorithm happens to be ridiculously parallelizable, things will not work.

Check 
[http://folding.stanford.edu/](http://folding.stanford.edu/)

and 

[http://setiathome.berkeley.edu/](http://setiathome.berkeley.edu/)

Those two do come with very paralleizable algorithms.

---

### Post by jwbrase on 2011-12-24
> **3Miro said:**
> Supercomputers are useful for scientific applications, however, an Internet based supercomputer has very limited use. The biggest drawback in supercomputing is the high cost of communication between the machines, that is on a local 2x1Gb network. On the Internet, unless your algorithm happens to be ridiculously parallelizable, things will not work.

Ridiculous parallelism is the defining feature of modern supercomputers. Problems that don't benefit from massive parallelism are probably going to be done on high-end desktops rather than supercomputers in the first place.

---


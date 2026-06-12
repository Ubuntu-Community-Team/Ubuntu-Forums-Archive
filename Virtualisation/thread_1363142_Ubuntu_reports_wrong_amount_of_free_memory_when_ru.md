---
title: "Ubuntu reports wrong amount of free memory when running Vmware Server"
date: 2009-12-24
forum: Virtualisation
---

### Post by HDave on 2009-12-24
I am running 9.04 with VMware server 2.0 on a machine with 8 core and 16GB of memory.  Everything is working fine...no complaints except one.  The system monitor, conky, and the "free" command all consistently report that 90% of memory is free with only 1.6GB taken up.  

This can't be right because I am running 15 virtual machine at once!  If I go into each machine and total the memory used, I get about 10 GB used.  Interestingly, the VI gui also says my machine is only using 1.6GB of RAM.

Any else seeing this?  or not seeing this?

---

### Post by darco on 2009-12-24
I used to see that too when running Conky. Its fine now so it was either fixed after I upgraded to 9.10 or when I upgraded to vmware 7....
good luck


darco

---


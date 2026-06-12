---
title: "evaluate eucalyptus"
date: 2013-01-21
forum: Ubuntu Cloud and Juju
---

### Post by asraa on 2013-01-21
after i build eucalyptus private cloud i want to do performance evaluation of my eucalyptus cloud like cpu utilization , memory usage , virtual machine performance , disk I/O ....etc
 
how can i do this , what are the benchmarks used to ecaluate the eucalyptus and how to implement them   please share your information .
 
thank you in advance

---

### Post by tgalati4 on 2013-01-21
If this is for home use, then simply create your own metrics.  Copying files, streaming media, etc.  Just post the throughput that you get and others will chime in with what they get with other solutions such as freenas, commercial NAS boxes, and enterprise server equipment.

phoronix-test-suite will give you performance benchmarks on the hardware itself, but your performance over your own network will depend on several factors and is unique to your situation.  So all that really matters is MegaBytes/second throughput.

---


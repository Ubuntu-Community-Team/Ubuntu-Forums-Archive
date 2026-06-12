---
title: "Implementing a new real time I/O disk scheduler"
date: 2013-11-12
forum: Ubuntu Dev Link Forum
---

### Post by varunkumhar2 on 2013-11-12
Hi,

I would like to implement a new I/O disk scheduler for Ubuntu in addition to the existing Deadline, Noop and CFQ schedulers. My scheduler would be a real time scheduler considering the deadline of incoming I/O requests, before granting disk access. From my research, i found that the schedulers are defined in the sched.c file. But i am unable to find these files in my Ubuntu 12.04. Kindly let me know the procedure to approach my problem and the set of files to be modified to implement my new I/O scheduling algorithm.

Thanks,
Varun

---

### Post by tgalati4 on 2013-11-12
Have you enabled the "source" repositories?  They are not selected by default.  Perform an update then install the source code for the linux kernel.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by varunkumhar2 on 2013-11-12
Thanks a lot for your reply. How can we enable the source repositories? Do we have to set an attribute in the config files before building the kernel?

---


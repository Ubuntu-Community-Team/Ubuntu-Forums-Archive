---
title: "VMWare Server 2.0.1 and Ubuntu?"
date: 2009-04-03
forum: Server Platforms
---

### Post by Brazilian Joe on 2009-04-03
Dear all,

I have noticed that VMWare Server 2.0.1 has been published, and along with that we should have some good stuff coming along. One of the things that usually comes is a new version of VMWare Tools, and with that compatibility with the latest kernels.

VMWare Tools from Server 2.0 had trouble compiling against kernels past the LTS version (2.6.24), So we had trouble using 8.10 (2.6.27), and 9.04 (still in beta) - what kernel does it use? 2.6.28, 2.6.29, 2.6.30?

I believe at least 8.10 and kernel 2.6.27 will be supported, and I will be very happy to learn that 9.04 works too - if it happens.

has anyone had time to upgrade VMWare Server to 2.0.1? Can anyone share some light in the subject? 

I have read the release notes, but I haven't found any mention of kernel compatibility and such.

---

### Post by blazerte on 2009-04-05
VMware Server V2.0.1 compiles with my kernel 2.6.28.x but not with kernel 2.6.29.1 :

/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:67: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’

... and so on for the other id's

---

### Post by schettj on 2009-04-05
Some unofficial patches on the vmware forums

[http://communities.vmware.com/thread/188410](http://communities.vmware.com/thread/188410)

I've not yet tried these. My main vmware server is on an LTS kernel...

---

### Post by blazerte on 2009-04-05
Actual patches I've seen are for the workstation, not server code. 

Although parts (the id stuff, smp_wait_function) may work, there's nothing about the poll_initwait problem.

One guy has a complete set of replacement modules for Server V2.0.0, but whether that works for 2.0.1, I dunno. He didn't report the poll_initwait error either, so maybe not.

---


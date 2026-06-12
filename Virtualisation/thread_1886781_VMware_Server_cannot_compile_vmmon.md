---
title: "VMware Server cannot compile vmmon"
date: 2011-11-25
forum: Virtualisation
---

### Post by glug101 on 2011-11-25
Greetings all!

I am attempting to setup a headless VM Server, however, the install fails while attempting to compile the vmmon module.

I'm currently running Ubuntu 10.04 Server and using VMware Server version 2.0.2.  I've followed the many guides available on these forums and others.  Still not able to get the module to compile. 

Any help would be appreciated.  I'd even accept suggestions of other software that might work well as VM Server.

Thanks in advanced!

---

### Post by gordintoronto on 2011-11-25
It would help if you said how the compile fails. Did you install build-essential?

---

### Post by chulik on 2011-11-29
Hi! Unfortunately, I have the same problem. So,
1. 
# cat /etc/issue
Ubuntu 11.10 \n \l

# cat /etc/debian_version 
wheezy/sid

# uname -a
Linux work 3.0.0-13-generic-pae #22-Ubuntu SMP Wed Nov 2 15:17:35 UTC 2011 i686 i686 i386 GNU/Linux

# vmware -v
VMware Server 2.0.2 build-203138

2. 
# dpkg -l ...
ii  build-essential                        11.5ubuntu1
ii  linux-headers-3.0.0-13-generic-pae     3.0.0-13.22 

3. Trouble:

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 3.0.0-13-generic-pae).  Even if the module were to
compile successfully, it would not load into the running kernel.

---


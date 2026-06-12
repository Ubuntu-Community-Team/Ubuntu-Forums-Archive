---
title: "Limit on the number of processors?"
date: 2010-05-06
forum: Server Platforms
---

### Post by jlsham on 2010-05-06
I have a server with 48 cores, 8 6-way Opteron CPU's. Ubuntu Server 9.04 only sees 32 processors. Is there a limit on the number of cores/processors that the server will use? Windows 2008 on the same server sees all 48 cores and the so does the BIOS, so this is unique to Ubuntu right now. A quick forum search didn't turn up anything, so any help would be appreciated - thanks.

---

### Post by windependence on 2010-05-06
AFAIK, 

1.Intel x86:
Maximum CPUs: 32 (including logical CPUs)
Maximum memory: 64GB
Maximum filesize: 8TB
Maximum filesystem size (ext3) 16TB
Maximum per-process virtual address space: 4GB


 2.AMD64/EM64T:
Maximum CPUs: 64
Maximum memory: 128GB
Maximum filesize: 8TB
Maximum filesystem size (ext3): 16TB
Maximum per-process virtual address space: N/A

Yep, you are over the number of cores for the 32 bit version. Loading 64 bit should get you there. 

-Tim

---

### Post by jbrown96 on 2010-05-06
Windependence, I imagine someone that's running serious hardware like that would not be using x86. 
I think the limit for the Linux kernel is like 128 CPUs, but I think that's physical, not cores. How are you checking the CPU count (cat /proc/cpuinfo)? If you are trying to use some userland tool, then it's likely that they don't report correctly; better to check with the kernel. 

On a side note, I don't think that Ubuntu is a very appropriate distro for a server like that. I'd be looking at something that is more tuned for your hardware.

---

### Post by windependence on 2010-05-06
Open Solaris would probably be my choice, followed by CentOS.

-Tim

---

### Post by windependence on 2010-05-06
Sorry, my bad:

**AMD 64/EM64T (CentOS 5.x/RHEL 5.x Linux specific info) **

 
[LIST]
[*]Maximum CPUs: 256
[*]Maximum memory: 256GB
[*]Maximum filesize: 8TB
[*]Maximum [filesystem  size]("http://www.cyberciti.biz/howto/question/static/maximum-partition-size.php") (ext3): 16TB
[*]Maximum per-process virtual address space:  N/A
[/LIST]

-Tim

---

### Post by jlsham on 2010-05-10
Thanks for the help. I was using a GUI tool to look and it only sees 32 cpus, but the CLI you suggested shows all 48. I'm gonna stay with Ubuntu 64 bit server for now, Centos is my preferred distribution but all of the people that login are more comfortable with Ubuntu.

---


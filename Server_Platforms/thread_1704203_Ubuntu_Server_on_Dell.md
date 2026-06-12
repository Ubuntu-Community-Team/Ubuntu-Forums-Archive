---
title: "Ubuntu Server on Dell"
date: 2011-03-10
forum: Server Platforms
---

### Post by wannymahoots on 2011-03-10
I was wondering if anyone could help advise about installing ubuntu server on a 4-socket dell rack server?  The server is a PowerEdge R815 and will contain 4 8-core 2.3Ghz AMD processors, along with 64Gb (8 x 8Gb Dual Ranked RDIMM) of RAM.

Web page for the server here:
[http://www.dell.com/uk/business/p/poweredge-r815/pd?cs=ukbsdt1&s=bsd&refid=poweredge-r815&s_tnt=34648:1:0](http://www.dell.com/uk/business/p/poweredge-r815/pd?cs=ukbsdt1&s=bsd&refid=poweredge-r815&s_tnt=34648:1:0),

It would be very useful if we could know in advance (i.e. prior to ordering!) whether Ubuntu server would likely run on this machine, and what if any complications might arise.  Specifically, I am concerned (someone mentioned to me) that the standard kernel may not scale to 32 processors.  Any help very much appreciated.

---

### Post by mciverza on 2011-03-10
A quick google for 'ubuntu dell R815' returned this page: [http://www.ubuntu.com/certification/hardware/201008-6448]("http://www.ubuntu.com/certification/hardware/201008-6448")

which states > The Dell PowerEdge R815 server has been awarded the status of Ready on Ubuntu 64-bit PC (x86_64)

That link has other useful sections, so I recommend bookmarking it.

---

### Post by wannymahoots on 2011-03-10
Great, I must have missed that. I'm guessing, but I assume that "ready" means that the standard kernel will work all the way up to 48 processors on this machine?

I found this post which suggests that it should anyway...: 
[http://ubuntuforums.org/showthread.php?t=1475357](http://ubuntuforums.org/showthread.php?t=1475357)

---

### Post by mciverza on 2011-03-10
64-bit kernel. Yes. 
[URL="https://answers.launchpad.net/ubuntu/+question/9820"]
Launchpad Answer[/URL]

> AMD64/EM64T:
Maximum CPUs: 64
Maximum memory: 128GB
Maximum filesize: 8TB
Maximum filesystem size (ext3): 16TB
Maximum per-process virtual address space: N/A


(Don't forget to mark this thread "SOLVED").

---


---
title: "Issue affecting some Skylake/Kaby Lake processors"
date: 2017-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2017-06-26
[http://news.softpedia.com/news/debian-devs-urge-intel-skylake-and-kaby-lake-users-to-disable-hyperthreading-516654.shtml](http://news.softpedia.com/news/debian-devs-urge-intel-skylake-and-kaby-lake-users-to-disable-hyperthreading-516654.shtml)
and
[https://lists.debian.org/debian-devel/2017/06/msg00308.html](https://lists.debian.org/debian-devel/2017/06/msg00308.html)

From the second list:> This advisory is about a processor/microcode defect recently identified
on Intel Skylake and Intel Kaby Lake processors with hyper-threading
enabled.  This defect can, when triggered, cause unpredictable system
behavior: it could cause spurious errors, such as application and system
misbehavior, data corruption, and data loss.

It was brought to the attention of the Debian project that this defect
is known to directly affect some Debian stable users (refer to the end
of this advisory for details), thus this advisory.

Please note that the defect can potentially affect any operating system
(it is not restricted to Debian, and it is not restricted to Linux-based
systems).  It can be either avoided (by disabling hyper-threading), or
fixed (by updating the processor microcode).

---

### Post by mikodo on 2017-06-26
Thanks, vasa1.

I don't have an affected processor now but, I am planning to buy a new system with a Kaby Lake processor, that will probably be affected.  I'll be checking the new processor against the list of affected ones, as shown in the Debian Advisory. Shutting off hyper-threading in the BIOS isn't going to affect me.

---

### Post by henke54 on 2017-06-27
> Over the weekend, developers for the Linux distro, Debian, discovered a bug with Intel’s CPU microcode for Skylake and Kaby Lake. The issue can cause some systems to misbehave with Hyper-Threading enabled and lead to data corruption or loss. Given that Skylake and Kaby Lake have been around for quite some time, this isn’t an issue that is going to be widespread. However, the exact conditions that cause the error are unclear.
[https://www.kitguru.net/components/cpu/matthew-wilson/linux-devs-have-discovered-a-microcode-bug-with-intel-6th-gen-and-7th-gen-cpus/](https://www.kitguru.net/components/cpu/matthew-wilson/linux-devs-have-discovered-a-microcode-bug-with-intel-6th-gen-and-7th-gen-cpus/)
[https://lists.debian.org/debian-devel/2017/06/msg00308.html](https://lists.debian.org/debian-devel/2017/06/msg00308.html)

---

### Post by howefield on 2017-06-27
Threads merged.

---


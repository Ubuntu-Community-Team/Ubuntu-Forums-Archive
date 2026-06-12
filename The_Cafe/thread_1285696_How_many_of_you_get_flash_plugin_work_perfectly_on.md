---
title: "How many of you get flash plugin work perfectly on x64 firefox?"
date: 2009-10-08
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-10-08
I have tried adobe flash, gnash and swfdec, all of them only partially work. For example, the video of [http://www.nytimes.com/](http://www.nytimes.com/) and the [adobe flash homepage]("http://www.adobe.com/products/flashplayer/") never play. 

**Edit**: For those have a CPU which doesn't have the lahf_lm flag (usually non-Core architecture), please refer to this [HOWTO]("http://ubuntuforums.org/showthread.php?t=1263905"). It solved my problem.

For those doesn't work, please post your 
```
cat /proc/cpuinfo |grep flags 
```
so that we could know if lacking of lahf_lm is the cause of the failure

---

### Post by NoaHall on 2009-10-08
Mine works great. Follow the advice in my sig if you want more help.
There's 64 bit alpha flash, which is much better.

---

### Post by afeasfaerw23231233 on 2009-10-08
Thanks for your guide. That's what I exactly did in your instructions. 

May ask I what your CPU is? Some say that those CPU which aren't Core microarchitecture such as Pentium 4 and Athlon 64 without the lahf_lm flags don't work because they lack this instruction. 

Such as mine

```
cat /proc/cpuinfo |grep flags
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr

```
doesn't have lahf_lm, therefore it fails.

Here's the bug report from Gentoo
[http://bugs.gentoo.org/show_bug.cgi?id=286159](http://bugs.gentoo.org/show_bug.cgi?id=286159)

---

### Post by afeasfaerw23231233 on 2009-10-08
Wow! I've just found out this thread: [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
It works perfectly after downloading flashplugin-lahf-fix.tar.gz and run the C. Problem solved.

---

### Post by Crunchy the Headcrab on 2009-10-08
I use the Linux 64bit beta or whatever it's at now from adobelabs.  I've never had a problem with it on  Ubuntu 9.04 or on Fedora 11 Leonidas.

---

### Post by 3rdalbum on 2009-10-08
I use the 64-bit edition on a Core 2 without problems. Interestingly enough, I've installed it on a Sempron machine and it still works without any fiddling.

---

### Post by Eisenwinter on 2009-10-08
"Some doesn't some doesn't"?

---

### Post by Tibuda on 2009-10-08
Never had a problem. Things are even better with the 64bit alpha instead of the 32bit wrapper.

---

### Post by samjh on 2009-10-08
I use the 64-bit alpha-release Flash plugin, which works fantastically. :)

---

### Post by afeasfaerw23231233 on 2009-10-08
> **Eisenwinter said:**
> "Some doesn't some doesn't"?

Sorry, typo error. Cannot edit the content of the poll.

---

### Post by infestor on 2009-10-08
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy
```

after some time flash stops working or plays the videos really slow almost like a flash show :(

---


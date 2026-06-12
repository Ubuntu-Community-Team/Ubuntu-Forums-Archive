---
title: "What CFLAGS to use with my processor...."
date: 2009-02-07
forum: The Cafe
---

### Post by juanmoreno92 on 2009-02-07
Can anyone help me with what options I should use with my CPU? I plan to install Gentoo and need some helpful tips on what to use. Here is my CPU info.(I run x86_64 since I want to be "ahead of the game";)):
```
[Juan@linux64 ~]$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 2925.98
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 2925.87
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

[Juan@linux64 ~]$ 
```

---

### Post by crimesaucer on 2009-02-07
[http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel](http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel)
[http://www.gentoo.org/doc/en/gcc-optimization.xml](http://www.gentoo.org/doc/en/gcc-optimization.xml)
[http://en.gentoo-wiki.com/wiki/CFLAGS](http://en.gentoo-wiki.com/wiki/CFLAGS)
[http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)

---

### Post by juanmoreno92 on 2009-02-07
I was expecting some user input but the links work too.

---

### Post by BugenhagenXIII on 2009-02-08
It depends on whether or not you're going 64-bit

From the first link crimesaucer posted:

32-bit:
CFLAGS="-march=prescott -O2 -pipe -fomit-frame-pointer"
CXXFLAGS="${CFLAGS}"

64-bit:
CFLAGS="-march=nocona -O2 -pipe"
CXXFLAGS="${CFLAGS}"



That all the optimizations you'll really need.  Anything more than that tends to risk high instability with minimal speed gains.  That's not to say there aren't other cflags that would be usefull and/or safe, just that the speed gains from more than that are minimal.

---

### Post by k3rnelmustard on 2009-02-08
hmm, which version of gcc are you using?  If it's >= 4.2.2, you can use -march=native.  

```

-march=native -O2 -pipe -fomit-frame-pointer

```

is what I would do.  Even if you're running 64bit, AFAIK -fomit-frame-pointer is just already included, so you can leave it out if you'd like.  If you're running 32bit, definitely leave it in.  I've been using this for as long as it's been supported and it works well.

---

### Post by juanmoreno92 on 2009-02-09
I am going 64-bit and I use GCC 4.3.2. Also on the opt flags that I could use, would -msse2 be any good? Oh and since my processor is based on the Core 2 architecture should I use -march=core2 or -march=nocona? GCC 4.3.2 gives the new option of core2.

---

### Post by kk0sse54 on 2009-02-09
Why don't you ask on the Gentoo forums?

---

### Post by jdong on 2009-02-09
> **juanmoreno92 said:**
> I am going 64-bit and I use GCC 4.3.2. Also on the opt flags that I could use, would -msse2 be any good? Oh and since my processor is based on the Core 2 architecture should I use -march=core2 or -march=nocona? GCC 4.3.2 gives the new option of core2.

To be honest apart from -march=native vs -march=core2 suggestions, I wouldn't add anything above the listed safe CFLAGS for system-wide flags... Back when I was a gentoo user and forums participant, I can't tell you how many weird system issues (KDE apps randomly crashing, etc) eventually traced down to a CFLAG. It isn't worth the headaches to push these too far on a system-wide basis; but for individual programs it can be worth it to try a bunch of aggressive CFLAGs and benchmark them against each other. You may be surprised at the results, though.

---

### Post by binbash on 2009-02-09
Before Installing gentoo not only cflags also make your use flags then start installing gentoo.Otherwise when you are tweaking your box , you will recompile the whole world.Also ubuntuforums is not a good place to ask this, use gentoo forums instead

---

### Post by juanmoreno92 on 2009-02-09
Well thanks for the suggestions guys. I installed it successfully on a second partition in my HDD.

---


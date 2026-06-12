---
title: "[SOLVED] need some information for including swiftfox in Automatix"
date: 2006-05-27
forum: The Cafe
---

### Post by arnieboy on 2006-05-27
guys,
        I need the output for the following command
```
cat /proc/cpuinfo
```
for the following processors:
> AMD Duron
AMD Athlon Thunderbird
AMD Duron Spitfire
AMD K6-2


I need this information for including swiftfox in automatix. I thank everyone in advance for his/her help.

---

### Post by wyohermit on 2006-05-27
Arnieboy

wyohermit@Dapper:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 2
cpu MHz         : 448.207
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 896.99

---

### Post by GazzaK on 2006-05-27
Arnieboy - 

> garyke@dogbert:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2500+
stepping        : 0
cpu MHz         : 1837.438
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3677.62

---

### Post by WildTangent on 2006-05-27
> 
admin@s1:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 6
cpu MHz         : 999.111
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1978.36


-Wild

---

### Post by tomothy on 2006-05-27
Arnieboy -

> 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1500MHz
stepping        : 5
cpu MHz         : 1498.763
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1199.60



---

### Post by WildTangent on 2006-05-27
Just in case you need this too:

> 
justin@the-siren:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2400.098
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4803.72

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 2400.098
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy
bogomips        : 4799.69


-Wild

---

### Post by Iandefor on 2006-05-27
ian@leviathan:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 2600+
stepping        : 2
cpu MHz         : 1999.911
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4004.12

EDIT: Damn you, Wild, for having a dual-core!

---

### Post by mstlyevil on 2006-05-27
[QUOTE=Iandefor]ian@leviathan:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 2600+
stepping        : 2
cpu MHz         : 1999.911
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 4004.12

EDIT: Damn you, Wild, for having a dual-core![/QUOTE]

Dual cores are overrated. (Only because I do not have one! :mrgreen: )

---

### Post by mstlyevil on 2006-05-28
bump :mrgreen:

---

### Post by aktiwers on 2006-05-28
Heres mine:

> 
aktiwers@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2800+
stepping        : 0
cpu MHz         : 2088.140
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow ts
bogomips        : 4181.76

aktiwers@ubuntu:~$


---

### Post by picpak on 2006-05-28
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 7
model name      : Pentium III (Katmai)
stepping        : 3
cpu MHz         : 500.962
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1002.68

---

### Post by John.Michael.Kane on 2006-05-28
Arnieboy here you go if need this version.
[QUOTE=]processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : Mobile AMD Athlon(tm) 64 Processor 2800+
stepping        : 0
cpu MHz         : 1800.049
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnowbogomips        : 1600.60[/QUOTE]

---

### Post by WildTangent on 2006-05-28
Here's another from my brothers PC using a livecd :D

> 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 7
model name      : mobile AMD Duron(tm)
stepping        : 1
cpu MHz         : 1200.192
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 2366.12


Here's some more info on the CPU:
[http://w1ldt4ng3nt.net/files/cpuz_duron.htm](http://w1ldt4ng3nt.net/files/cpuz_duron.htm)

-Wild

---

### Post by mstlyevil on 2006-05-29
Bump again

---

### Post by henriquemaia on 2006-05-29
[quote=mstlyevil]Bump again[/quote] 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Athlon(tm) 64 Processor 3700+
stepping        : 1
cpu MHz         : 2210.220
cache size      : 1024 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 2010.59
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

### Post by mstlyevil on 2006-05-29
Bump (Silly isn't it) :mrgreen:

---

### Post by WildTangent on 2006-05-29
What CPUs do you still need?

-Wild

---

### Post by arnieboy on 2006-05-29
[QUOTE=WildTangent]What CPUs do you still need?

-Wild[/QUOTE]
the ones in the first post. mstlyevil updated it.

---

### Post by mstlyevil on 2006-05-29
bumpity bump bump bump

---

### Post by WildTangent on 2006-05-29
Got a tbird for you:

> 
cat /proc/cpuinfo:
 processor : 0
 vendor_id : AuthenticAMD
 cpu family : 6
 model : 4
 model name : AMD Athlon(tm) Processor
 stepping : 4
 cpu MHz : 1333.382
 cache size : 256 KB
 fdiv_bug : no
 hlt_bug : no
 f00f_bug : no
 coma_bug : no
 fpu : yes
 fpu_exception : yes
 cpuid level : 1
 wp : yes
 flags : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36
mmx fxsr syscall mmxext 3dnowext 3dnow
 bogomips : 2660.76 


Additionally, this page may be of help, you might be able to use the CPU family and model numbers:
[http://www.paradicesoftware.com/specs/cpuid/index.htm](http://www.paradicesoftware.com/specs/cpuid/index.htm)

-Wild

---

### Post by WildTangent on 2006-05-29
Holy crap...I finished it... "The (almost) Be All, and End All List for Information Regarding CPUs in Relation to Including Swiftfox in Automatix", or BAEALIRCPURISA for short... :-P

[http://www.w1ldt4ng3nt.net/files/cpuid.html](http://www.w1ldt4ng3nt.net/files/cpuid.html)

I really REALLY hope that helps arnieboy... I spent the better part of 2 hours gathering that info...

If theres anything incorrect, please correct me :)

Now, in order to use this information for Automatix, you will need to grep cpuinfo for the vendor string, the family number, and for most of these CPUs, the model number.

-Wild

---

### Post by betty on 2006-09-07
Arnieboy:

Automatix does not allow installation on a classic athlon (not thunderbird) because "processor architecture is not supported".  The architectures of the classic athlon and thunderbird are identical, except that the cache on the thunderbird runs at full speed of the processor while the athlon classic is at 1/3, and the cache on the athlon cassic is twice that of the thunderbird.  I've installed swiftfox successfully from the deb on my classic athlon, and the speed difference is very noticeable.  But I can't use automatix to do it, and I can't use automatix to install the swiftfox plugins because the destination directories were different from the deb install.  Any way you could add the classic athlon to allow automatix to install it?  It would get the same swiftfox as Athlon thunderbird.  Here is my output:

Thanks!
betty

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 2
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 948.315
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
bogomips        : 1898.41

---


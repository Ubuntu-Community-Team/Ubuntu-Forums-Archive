---
title: "I think my fan is running faster than normal"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-09-29
1st speedup is at 46C
2ed speedup is at 55C 
3ed at 65C
4th at 80C (this is probably max)
speed drops when it hits 70C
speed drops again at 55C
it will not cool enough to slow down more
this laptop will idle in the mid 50C
critical temp is 120C
```
~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 17
model        : 3
model name    : AMD Athlon Dual-Core QL-62
stepping    : 1
microcode    : 0x2000057
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate lbrv svm_lock nrip_save
bogomips    : 4000.00
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 17
model        : 3
model name    : AMD Athlon Dual-Core QL-62
stepping    : 1
microcode    : 0x2000057
cpu MHz        : 1000.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit hw_pstate lbrv svm_lock nrip_save
bogomips    : 4000.00
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate
```

---

### Post by Rukiri on 2012-09-29
May I ask what you were doing when it was speeding up?   But judging from your CPU(which I'm going to assume it's 32Bit) is having a high workload, unity seems to have a larger footprint than Gnome 3.

May I ask what DE you're using? install xfce and boot into the xfce session and see if that helps.

---

### Post by pqwoerituytrueiwoq on 2012-09-29
64bit Athlon II 2Ghz
xubuntu 12.10 beta 2 all updates installed
to get to 55C it just idles from a cold boot
to get to 80C+ i used the linux version of prime95
to hit 65 i played hedgewars (800x600@30fps) (youtube will do this easly)
link to laptop specs in signature
my gpu idles 10-20C above the cpu 
gpu=geforce 8200m
nvidia-settings:  version 304.37

---

### Post by effenberg0x0 on 2012-09-29
I think it's important to test if you have working Nvidia/Nouveau drivers before tweaking other stuff. In QQ one can easily be switched to llvmpipe after updates without any warning.
 
```
sudo apt-get install nux-tools
/usr/lib/nux/unity_support_test -p

```

You gotta check if you have "OpenGL vendor string:   NVIDIA Corporation", or something else.

Regards,
Effenberg

---

### Post by pqwoerituytrueiwoq on 2012-09-29
by the time i login my cpu is at 50C from a cold boot i used suspend to find the lower number
attached screenshot that is what you meant right?

should i still use unity_support_test even thought i am not using unity/gnome/compiz/cinnamon?

edit: it was a small download and i had all the dependencies so i installed it 

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8200M G/integrated/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.43

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---


---
title: "High perfromance server - need a cool idea"
date: 2010-01-24
forum: The Cafe
---

### Post by SeanTater on 2010-01-24
A friend of mine just built a high performance server:
Dual- Quad-core Opteron CPU (/proc/cpuinfo available if necessary)
16 GB RAM (don't know what speed)
No special HD, just 120 GB (probably SATA)

He gave me an account to it (because I helped him troubleshoot some problems he was having) and I can't think of anything cool to do with it.. So far I have some up with:

* Minting an impressive hash collision using hashcash (maybe 42-45 bits?)
* Getting Folding at Home stats
* Encoding an x264 HD video

All those things take time and CPU resources but they don't seem all that cool. They also don't seem to take advantage of the fact that all eight cores are on the same computer.. Does anyone have ideas what else I could run?

---

### Post by pirateghost on 2010-01-24
install ESXi on it and run 30 virtual machines of whatever you want  ;)

---

### Post by philcamlin on 2010-01-24
get 5 monitors, install 5 diff os'es 
and play a game on each :D

---

### Post by SeanTater on 2010-01-24
Actually the virtualization sounds cool - I think I might try that!
The games probably wouldn't work though - the server is in another state, so the internet link wouldn't be able to handle the video.

Thanks - and I'm still listening if anyone else has ideas!

---

### Post by The Real Dave on 2010-01-24
Well, that beats my [server]("http://linuxexpresso.wordpress.com/hardware")... :(

Do some mad Folding@Home, SETI@Home, encode some really high def movies :) That should push it :) Can we get some pics? :)


Oh, install SuperPI and see how long it takes to calculate PI to a million places :) Then but the results here as a brag fest :)

---

### Post by k64 on 2010-01-24
sudo apt-get install apache2 mysql php-http

---

### Post by danwosere2007 on 2010-01-24
O.k hows about.....First of all take the server and attach a snowboard to the bottom of it, then get it into a plane and fly up to about 30,000 feet above the french alps, jump out of the plane with it, bust a few sick airborne manoeuvres with ya server and when it gets to a suitably death defying low altitude, pull the rip cord causing the server to land atop a precarious piste. Pull a few gnarly 1080's with the server inadvertedly triggering an enormous avalanche, ride your server down this wave of snow all the way to the bottom of the valley. Then plug in the server and see if it still works. =P

---

### Post by tgalati4 on 2010-01-24
If it's a 1 RU server, then that is the snowboard.  Screw in some foot locks and you are good to go.

---

### Post by marin123 on 2010-01-24
you can go to town with your server and pick up some chicks... i think, no i know that their panties will fly away when you show them your server :D

---

### Post by mr clark25 on 2010-01-24
i like the idea of super pi. you could really have some bragging rights there ;)

---

### Post by SeanTater on 2010-01-24
Ha! I couldn't imagine trying to snowboard with a server - but it sounds like a good excuse to take a vacation to Europe!
It's not a rack mounted server unfortunately - actually, it's in a makeshift plastic bin with a few fans. (I'll see if I can get a picture of it..) My friend just happened on the parts and decided it was impossible to pass up.

As for the super PI - I'll see what I can do.. Thanks for the ideas guys!

EDIT: Super PI seems to be for Windows, and it's single threaded.. Am I missing something? (The server runs Ubuntu BTW)

---

### Post by MaxIBoy on 2010-01-24
No, there's a Linux version. I think it comes with the Phoronix Test Suite as well.


If your friend is okay with you chewing through the CPU, try getting into 3D modeling and render stuff with it.

---

### Post by SeanTater on 2010-01-24
Oops! Sorry guys! I put the wrong specs up... (Goes to show I haven't actually seen the thing)

It has 16 cores on 4 processors, not 8 cores on 2 processors... Here's the /proc/cpuinfo:
```
processor       : 0                         
vendor_id       : AuthenticAMD              
cpu family      : 16                        
model           : 2                         
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 0                                       
siblings        : 4                                       
core id         : 0                                       
cpu cores       : 4                                       
apicid          : 0                                       
initial apicid  : 0                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4620.72                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 0                                       
siblings        : 4                                       
core id         : 1                                       
cpu cores       : 4                                       
apicid          : 1                                       
initial apicid  : 1                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4641.87                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 0                                       
siblings        : 4                                       
core id         : 2                                       
cpu cores       : 4                                       
apicid          : 2                                       
initial apicid  : 2                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4641.74                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 0                                       
siblings        : 4                                       
core id         : 3                                       
cpu cores       : 4                                       
apicid          : 3                                       
initial apicid  : 3                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4641.74                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 4
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 1                                       
siblings        : 4                                       
core id         : 0                                       
cpu cores       : 4                                       
apicid          : 4                                       
initial apicid  : 4                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.67                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 5
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 1                                       
siblings        : 4                                       
core id         : 1                                       
cpu cores       : 4                                       
apicid          : 5                                       
initial apicid  : 5                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.70                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 6
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 1                                       
siblings        : 4                                       
core id         : 2                                       
cpu cores       : 4                                       
apicid          : 6                                       
initial apicid  : 6                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.63                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 7
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 1                                       
siblings        : 4                                       
core id         : 3                                       
cpu cores       : 4                                       
apicid          : 7                                       
initial apicid  : 7                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.69                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 8
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 2                                       
siblings        : 4                                       
core id         : 0                                       
cpu cores       : 4                                       
apicid          : 8                                       
initial apicid  : 8                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4637.53                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 9
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 2                                       
siblings        : 4                                       
core id         : 1                                       
cpu cores       : 4                                       
apicid          : 9                                       
initial apicid  : 9                                       
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4637.78                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 10
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 2                                       
siblings        : 4                                       
core id         : 2                                       
cpu cores       : 4                                       
apicid          : 10                                      
initial apicid  : 10                                      
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.42                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 11
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 2                                       
siblings        : 4                                       
core id         : 3                                       
cpu cores       : 4                                       
apicid          : 11                                      
initial apicid  : 11                                      
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.66                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 12
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 3                                       
siblings        : 4                                       
core id         : 0                                       
cpu cores       : 4                                       
apicid          : 12                                      
initial apicid  : 12                                      
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.80                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 13
vendor_id       : AuthenticAMD
cpu family      : 16          
model           : 2           
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3                                       
cpu MHz         : 2310.365                                
cache size      : 512 KB                                  
physical id     : 3                                       
siblings        : 4                                       
core id         : 1                                       
cpu cores       : 4                                       
apicid          : 13                                      
initial apicid  : 13                                      
fpu             : yes                                     
fpu_exception   : yes                                     
cpuid level     : 5                                       
wp              : yes                                     
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs                         
bogomips        : 4638.21                                                                                                                                                           
TLB size        : 1024 4K pages                                                                                                                                                     
clflush size    : 64                                                                                                                                                                
cache_alignment : 64                                                                                                                                                                
address sizes   : 48 bits physical, 48 bits virtual                                                                                                                                 
power management: ts ttp tm stc 100mhzsteps hwpstate                                                                                                                                

processor       : 14
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3
cpu MHz         : 2310.365
cache size      : 512 KB
physical id     : 3
siblings        : 4
core id         : 2
cpu cores       : 4
apicid          : 14
initial apicid  : 14
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips        : 4639.36
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor       : 15
vendor_id       : AuthenticAMD
cpu family      : 16
model           : 2
model name      : Quad-Core AMD Opteron(tm) Processor 8356
stepping        : 3
cpu MHz         : 2310.365
cache size      : 512 KB
physical id     : 3
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 15
initial apicid  : 15
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips        : 4638.39
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```


And to prove it, I added the photo (before it had a case)

---

### Post by mr clark25 on 2010-01-24
wow! that thing is a monster!

---

### Post by The Real Dave on 2010-01-24
</drool> Nice!! Ya, that kinda beats my 1.7Ghz PIV server alright ;) Where do you buy parts for something like that?

Funky keyboard BTW :)

---

### Post by mr clark25 on 2010-01-24
i saw that newegg was selling a dual-core lga 1366 motherboard.

awhile later, i saw an 8-core server (had 2 lga 1366 quad-core xeons) show up on a benchmarking site witha benchmark of over 22,000! the core i7 975's only get 7500 or so.

---


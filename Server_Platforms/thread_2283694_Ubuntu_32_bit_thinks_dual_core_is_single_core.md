---
title: "Ubuntu 32 bit thinks dual core is single core"
date: 2015-06-23
forum: Server Platforms
---

### Post by do.marmor on 2015-06-23
I decided to retire my single core server and build a new using a Acer Aspire M1640 2ghz dualcore 3GB Ram (i will upgrade ram later)  

i installed using the 32bit version of ubuntu and everything work t fine but after awhile the server froze on me.

 i found out that Ubuntu only find and use one of the two cores ,after reading everything i can find about the subject it seems this is a problem only exist on 32 bit version of Ubuntu and after several hours looking i did not find one working solution to fix the problem other then installing 64bit 
hopefully someone here knows a working solution,

So question is how do i get ubuntu-14.04.2-server 32 bit to find and use both cores? and is it worth the trouble will 64 bit be just as fast?

---

### Post by darkod on 2015-06-23
Are you sure it detects only one core? How many cores does this command report:
```
cat /proc/cpuinfo | grep 'model name'
```

---

### Post by sudodus on 2015-06-23
I think 64-bit will be as fast or slightly faster, but will eat more RAM for the same task (compared to 32-bit). But with 3 GB RAM it should be OK. I think it is worth the trouble.

- How did you find out that the 32-bit version finds only one core? Did you use ***htop***? If not, it is worth trying what it will tell. See the attached file.

- Did you try with a 64-bit desktop version running live, that it finds both cores? Or are you only hoping that it will work?

---

### Post by do.marmor on 2015-06-26
sorry for the delay i been trying basically everything i found online about similar problem

```
cat /proc/cpuinfoprocessor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 22
model name      : Intel(R) Celeron(R) CPU          440  @ 2.00GHz
stepping        : 1
microcode       : 0x32
cpu MHz         : 2000.123
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
bogomips        : 4000.24
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
```

> **sudodus said:**
> 
- Did you try with a 64-bit desktop version running live, that it finds both cores? Or are you only hoping that it will work?

I was more like assuming/hoping some of the posts i was founding online claimed 64bit would work but i tried that now using live CD desktop version absolutely no change still just one cpu core, i also attempted to reinstall ubuntu server from basic (clean install) no result

this tower is very quiet unlike my old single core server, it also have built in hardware raid in the bios so perfect to build a server from, so i really hope there is a solution to the cpu problem atm it looks like ubuntu don't like Acer

---

### Post by cariboo on 2015-06-26
According to [this]("http://ark.intel.com/products/29736/Intel-Celeron-Processor-440-512K-Cache-2_00-GHz-800-MHz-FSB"), your cpu is only a single core device.

---

### Post by sudodus on 2015-06-26
These output indicate there is only one core. Are you sure there are two of them? What do other operating systems show?

There might be a problem both with managing the CPU and the system on the motherboard.

---

### Post by do.marmor on 2015-07-02
weird the problem is solved now as u can see on the ss.
I do not know how but it could have been hardware problem . i replaced some of the memory and was putting in a more quiet cooling system , restarting and all the sudden i got two cores.
But before that i also played around with the files trying to find the problem so what actually fixt the problem in the end i cant say but im guessing hardware, Ubuntu never gave me this type of problem in the past. either way ty all for trying to help.

---


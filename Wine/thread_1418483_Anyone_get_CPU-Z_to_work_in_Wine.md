---
title: "Anyone get CPU-Z to work in Wine?"
date: 2010-02-28
forum: Wine
---

### Post by paul7net on 2010-02-28
When I try it, it displays an error message saying

A previous version of the device driver is already running. This program requires driver version 1.32.

And then it displays CPU-Z with all the text boxes blank.

---

### Post by hikaricore on 2010-02-28
You might want to tell us a bit about what "cpu z" is.

I'm gussing this involves windows drivers and specialized hardware however and these sorts of applications do not generally work under wine.

---

### Post by pirateghost on 2010-02-28
> **hikaricore said:**
> You might want to tell us a bit about what "cpu z" is.

I'm gussing this involves windows drivers and specialized hardware however and these sorts of applications do not generally work under wine.

[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)

basically its unnecessary in linux anyway.  my guess is that the OP just doesnt know how to find out that info from normal linux methods

OP might benefit from having a look at conky or some of the applets for the gnome panel

---

### Post by kmsalex on 2010-02-28
this is cpu-z
[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)
is a program mostly utilised by overclockers that tells you detailed information about your cpu, and a little about you motherboard, memory and graphics. i don't think its possible as i don't think wine gives programs unrestricted access to you hardware.

---

### Post by paul7net on 2010-02-28
So since it won't work, what should I use to get all the processor goodies?

---

### Post by pirateghost on 2010-02-28
> **paul7net said:**
> So since it won't work, what should I use to get all the processor goodies?
what info do you need to know?

there are a lot of applets/screenlets/gui apps that can provide the info you want.

have a look at 'sysinfo' and 'system profiler and benchmark'
they can both be found in the Ubuntu software center

---

### Post by hikaricore on 2010-02-28
If you're simply looking to underclock/overclock your cpu you should do this at bios level or use a tool like powernow.

---

### Post by pirateghost on 2010-02-28
> **hikaricore said:**
> If you're simply looking to underclock/overclock your cpu you should do this at bios level or use a tool like powernow.
CPU-Z doesnt overclock.  it simply gives you the info on your hardware

---

### Post by NESFreak on 2010-03-19
You could get all the information you need by entering the following command in the commandline:
```
cat /proc/cpuinfo
```
for me this gives:
```
~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4189.54
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
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
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority
bogomips	: 4189.52
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

---

### Post by asdfoo on 2010-03-19
Set Wine to report Windows 98 in winecfg and cpu-z will run.

---

### Post by doorknob60 on 2010-03-20
Try using lshw, should give you everything you need (might need to get it from apt-get/synaptic first, not sure if it's installed by default).

---

### Post by Claus7 on 2011-02-09
Hello,

> **asdfoo said:**
> Set Wine to report Windows 98 in winecfg and cpu-z will run.

not as detailed the info it displays as a result of executing like this cpuz, yet at least it shows some.
That on 10.10.

Thanks,
Regards!

---

### Post by dino99 on 2011-02-09
cpu-g is the related cpu-z linux app

[http://gtk-apps.org/content/show.php/CPU-G?content=113796](http://gtk-apps.org/content/show.php/CPU-G?content=113796)

tested on natty i386 a few minutes ago and it work fine :)

---

### Post by Claus7 on 2011-02-09
Hello,

I confirm that cpu-g is working like a charm for maverick 64 bit too. The only problem I'm facing is that still(!) it does not show the frequency of the ram used! Neither the one that motherboard supports nor the one that is actually placed in the slot.

Maybe in the future this feature will be resolved.

Nice add on *dino99*,
Regards!

---

### Post by dino99 on 2011-02-10
agree 100 %,  the devs actively develop it and those missing features should appear soon :)

---


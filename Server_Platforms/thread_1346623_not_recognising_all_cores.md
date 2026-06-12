---
title: "not recognising all cores"
date: 2009-12-05
forum: Server Platforms
---

### Post by sdsykes on 2009-12-05
I have 2 Six-Core AMD Opteron processors in my server, but it only presents me with 8 cores rather than 12.  Is there a reason for this?

I have installed Ubuntu 9.04:

$ cat /proc/version
Linux version 2.6.28-11-server (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009

Here is an exctract from /proc/cpuinfo - this is core #7 - the last one listed.  Note it is a 6 core processor, but cpu cores is reported as 4.

processor	: 7
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 8
model name	: Six-Core AMD Opteron(tm) Processor 2431
stepping	: 0
cpu MHz		: 2400.068
cache size	: 512 KB
physical id	: 1
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 11
initial apicid	: 11
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 4800.29
clflush size	: 64
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by falconindy on 2009-12-05
what's the output of:
```
cat /sys/devices/system/cpu/kernel_max
```
The value returned +1 is the max number of cores the current kernel will support.

---

### Post by renkinjutsu on 2009-12-05
the kernel can support a maximum of 512 =]
you'll just have to compile your own kernel image (or ask someone to build you a deb)

---

### Post by sdsykes on 2009-12-06
> **falconindy said:**
> what's the output of:
```
cat /sys/devices/system/cpu/kernel_max
```
The value returned +1 is the max number of cores the current kernel will support.

Ok, thanks, but hum, that file is not there:

$ cat /sys/devices/system/cpu/kernel_max
cat: /sys/devices/system/cpu/kernel_max: No such file or directory
$ ls /sys/devices/system/cpu/
cpu0  cpu2  cpu4  cpu6  cpuidle  possible  sched_mc_power_savings
cpu1  cpu3  cpu5  cpu7  online   present
$

> **renkinjutsu said:**
> the kernel can support a maximum of 512 =]
you'll just have to compile your own kernel image (or ask someone to build you a deb)

Yes, ok so I guess there's not some simple config.  I'll investigate how to compile a kernel image (any pointers?)

Thanks!

---

### Post by renkinjutsu on 2009-12-06
there's a good guide for 9.04 [here]("http://easylinuxcds.com/blog/?p=3244"). Note, that if you're using 9.10 and grub2, updating the grub files manually is not needed, all you need to do is 'sudo update-grub' in console (but that happens automatically anyway, if you package it into a deb with make-kpkg before installing)

You can download a stable kernel from [kernel.org]("http://kernel.org"), or you can download the kernel source, patched by the Ubuntu team from the repositories.

when it's time to configure, i find using a GUI to configure much easier, so i cd into the kernel source and type 'make xconfig'.
The gui tool (and the make menuconfig tool for that matter) will save the configuration to a file '.config', and the vanilla kernel configuration might break your already working system, so it's a good idea to use Ubuntu's default configuration if you're doing this for the first time.. The configuration of your current kernel is located in /boot.. so if you're already in the kernel source directory
```
cat /boot/config-$(uname -r) > ./.config
``` should do the trick

Okay, so now, you can fire up 'make xconfig', locate "Processor type and features" on the left, and over on the right, you may want to select your processor family to make the kernel specific to your cpu, if you don't want it to be generic.

squint your eyes and skim through the configurations in the "Processor type and features" section. You should see something like ```
(8) Maximum number of CPUs
```

Double-click that and focus should be given to a bar somewhere below. Type in whatever number of CPUs you have, or more if you're going to add more.
save your configuration.

then, usual syntax would be ```
fakeroot make-kpkg --initrd --append-to-version=-somethinghere kernel_image kernel_headers
```
make sure you have a "-" before what you're appending to version number. Optionally, since you've got 8 CPUs in use, you can type ```
CONCURRENCY_LEVEL=8
``` and append the previous command to that ```
CONCURRENCY_LEVEL=8 fakeroot make-kpkg .. ...... .. *yadda yadda*
```

When it's done compiling, the deb files will be in the parent directory, so ```
cd ../
sudo dpkg -i *whateversthere*
```




If you're having trouble getting the GUI config tool to open up with 'make xconfig', that means you haven't installed QT and it's developmental packages

---

### Post by falconindy on 2009-12-06
> **renkinjutsu said:**
> If you're having trouble getting the GUI config tool to open up with 'make xconfig', that means you haven't installed QT and it's developmental packages
I've always found `make menuconfig` to be the easiest to deal with, as its entirely keyboard driven.

Also, more reference material on compiling kernels [here](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/). It's a slightly different method, but I've found it to be cleaner since you start with the default Ubuntu config, and not the kernel.org config.

---

### Post by sdsykes on 2009-12-07
Thanks for all your help, I'm confident I'll be able to config it correctly now.

---

### Post by renkinjutsu on 2009-12-07
i JUST found out about this..
a program [kernelcheck]("http://kcheck.sourceforge.net/") which pretty much makes everything automatic, with a little user input.

If you don't want to do everything yourself, you can try using kernelcheck.

---

### Post by trundlenut on 2009-12-07
+1 for kernelcheck, I used this on my laptop to compile a newer kernel that had support for my wireless network card.  It can take rather a long time to compile the kernel.

I found kernel check gives you plenty of options but does a lot of the hardwork for you.  I think you can use to it to compile a kernel for a different machine, so you can compile the server kernel on your desktop machine and it outputs a deb package you can install on the machine you want.

But not much use if you don't have a GUI on your server though.

---


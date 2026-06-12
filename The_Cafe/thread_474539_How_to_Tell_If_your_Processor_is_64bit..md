---
title: "How to Tell If your Processor is 64bit."
date: 2007-06-15
forum: The Cafe
---

### Post by Rhyn W on 2007-06-15
Hi I have an AMD Athlon 2800 runs at approx 2.0 ghz
I was given the chip and it went in place of my AMD sempron wthout any issues,
 must say major noticable difference.

But how do you know if your computer is 64bit capable?
And is changing to the new 64 bit worth it yet?
I plan on using it for home use its running Feisty Fawn at present.

Thank You anyone that can help me out here.

Rhyn

---

### Post by insane_alien on 2007-06-15
```
 cat /proc/cpuinfo

```

---

### Post by Rhyn W on 2007-06-15
Ok I'm new to Linux,

I'm the prime candidate if there ever was one for Linux for Dummies. 
But I know that Linux is not for dummies! No its for highly inteligent people right :-). 
So here I am learning and learning Quickly.

You have told me to enter some code, The code makes ssence onlything is the only place where I seem to be able to do that is when I boot in the restore mode. 
Is that how its done or is there a terminal you can open once inside Feisty Fawn you know once you've logged in. If there is, How do you open that?. 
Assuming there is and it opened I'm sure I can handle the code bit but just totally confuzzled as to how everyone talks code in this place and no one tell you where to or how to.

All I have is a desktop with applications places system and a web browser.
perhaps I should go and read some of the manuals BUT I"M A GUY I HATE MANUALS. But now like the dude without a map I'm lost and yes even asking for directions is a pain in the ...

If you read all this and feel like I deserve an answere then please feel free.
I won't blame you if you don't. seriously

Thanks for all the help anyway.

Regards

Rhyn W
aka slow learner...

---

### Post by angryfirelord on 2007-06-15
You have to go to Accessories-->Terminal. You can type it in there, or copy-paste the command. Pasting in a terminal is Shift+Ins, not Ctrl+V.

---

### Post by Rhyn W on 2007-06-15
Cool 
So I should be able to fix my permissions problems from that terminal aswell...
Big up thanks for the help.

Shot

Rw

---

### Post by init1 on 2007-06-15
Yes, many things can be done from the terminal. It is a very useful tool.

---

### Post by Rhyn W on 2007-06-15
from the info here can you tell if im 64 or 32bit machine.
I don't know what half this stuff means. Do You?
Processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2800+
stepping        : 0
cpu MHz         : 2082.676
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 4170.27
clflush size    : 32

---

### Post by S29K on 2007-06-15
I'm no CPU expert but I believe that the AMD Athlon XP CPUs are all 32-bit.  They started calling them AMD64 when they went 64-bit and the they came out with the X2 dual-core procs.

I also suspect that the clflush size: 32 is a good indication. ;)

---

### Post by Rhyn W on 2007-06-15
Thanks Man 
That makes life a little easyier hey !

Thank you kindly

---

### Post by forcesofhabit on 2007-06-15
Interesting... my clflush says 64... should I be running 64-bit Ubuntu??

---

### Post by a12ctic on 2007-06-15
If you want, 64bit has compatability issues with a lot of proprietary apps.

---

### Post by H.E. Pennypacker on 2007-06-15
> **forcesofhabit said:**
> Interesting... my clflush says 64... should I be running 64-bit Ubuntu??

I have an Intel Celeron M processor, and I am quite confident it is 32 bit processor, but  mine says 64 too (under clflush).  

The question has not been answered yet.   cat /proc/cpuinfo doesn't exactly answer the question, or doesn't seem to.

---

### Post by muguwmp67 on 2007-06-15
The next link discusses the differences between 32 and 64 bit ubuntu.
[https://help.ubuntu.com/community/32bit_and_64bit?highlight=%2864%29%7C%28bit%29]("https://help.ubuntu.com/community/32bit_and_64bit?highlight=%2864%29%7C%28bit%29")

I have an AMD64 too, but decided to go with the 32 bit version of Ubuntu because I did not want to deal with compatibility issues.  Running 32 bit Ubuntu on a 64 bit processor is fine.

---

### Post by a12ctic on 2007-06-15
> **H.E. Pennypacker said:**
> I have an Intel Celeron M processor, and I am quite confident it is 32 bit processor, but  mine says 64 too (under clflush).  

The question has not been answered yet.   cat /proc/cpuinfo doesn't exactly answer the question, or doesn't seem to.

there is a celeron m with 64bit now, but its very new.

---

### Post by ralphhughes on 2009-06-17
Old thread I know, but it turned up top in my google search for this topic. Have found from elsewhere a more reliable way is to type 
getconf LONG_BIT
This will return whether your CPU is 32 bit of 64 bit.

Ralph

---

### Post by Bachstelze on 2009-06-17
For Google's sake, yet another way is to do

```
cat /proc/cpuinfo
```

And search the "flags" line for the [font="monospace"]lm[/font] flag. If it is there, your processor is 64 bit.

---

### Post by Scruffynerf on 2009-06-17
> **ralphhughes said:**
> Old thread I know, but it turned up top in my google search for this topic. Have found from elsewhere a more reliable way is to type 
getconf LONG_BIT
This will return whether your CPU is 32 bit of 64 bit.

Ralph

I don't think that it does. The following is for my AMD64 cpu. And I run 32 bit linux.

Result of cat /proc/cpuinfo

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 12
model name	: AMD Athlon(tm) 64 Processor 3000+
stepping	: 0
cpu MHz		: 1999.976
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up lahf_lm
bogomips	: 3999.95
clflush size	: 64
power management: ts fid vid ttp

```

Result of getconf LONG_BIT

```
32
```

This would indicate that getconf is polling the software, not the hardware.

---

### Post by Rubicon_82 on 2009-06-17
Try:
```

lshw -C cpu

```

Look for the **width** tag.

---

### Post by Paqman on 2009-06-17
> **a12ctic said:**
> If you want, 64bit has compatability issues with a lot of proprietary apps.

The only apps i've found to be any problem on 64-bit are Adobe Air and Google Gears. Neither are available for 64-bit yet. I'm not sure about Air, but Gears definitely has an unofficial 64-bit version available.

---

### Post by CharmyBee on 2009-06-17
I haven't had much loss with 64-bit, other than the lack of Genesis playing (Gens and all forks do not support 64-bit CPU), and some x86 emulators running much slower.

---


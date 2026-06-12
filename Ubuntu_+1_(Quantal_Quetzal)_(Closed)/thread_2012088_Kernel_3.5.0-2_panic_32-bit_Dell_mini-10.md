---
title: "Kernel 3.5.0-2 panic 32-bit Dell mini-10"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fjgaude on 2012-06-28
Kernels 3.2 and 3.4 work fine but not 3.5. Get this:

Kernel panic - not syncing: Fatal exception in interrupt

Any ideas?

Thanks!

---

### Post by kevpan815 on 2012-06-28
I386 12.10 Alpha 2 working just fine on a Dell Inspiron 1012 Mini Net Book, Just FYI. No Kernel Modifications were made on that particular PC.

---

### Post by fjgaude on 2012-06-28
Thanks, and very interesting... but I do think that the 1012 has many different elements to it over my 10n. Is yours a Poulsbo chip set type?

Any ideas as to what I should try to see what the issue is?

---

### Post by lucazade on 2012-06-29
Same here fjgaude...
We should open a bug report .. btw I believe in kernel 3.5 there is some conflict between gma500_gfx and the acpi brightness support.

---

### Post by fjgaude on 2012-06-29
Okay, you go first! <smile>

---

### Post by KarmicKarmicChameleon on 2012-07-02
Did you guys ever submit a bug report? I'm having the same problem :(

---

### Post by DougieFresh4U on 2012-07-02
Had kernel panic as well on AMD64.
When I clicked on to submitt bug it stated one already existed.
I went and installed rc5 kernel and have not had kernel panic for over 24 hour period :p

---

### Post by jerrylamos on 2012-07-02
I'm not familiar with Dell mini-10
Could you do a 

cat /proc/cpuinfo

and post the results?  

I've a Acer Aspire 1 netbook in the other room running without panic (so far) I'll post its results when I fire it up.

Thanks,

Jerry

---

### Post by philinux on 2012-07-02
There is a new kernel in proposed. See sticky.

---

### Post by fjgaude on 2012-07-02
> **jerrylamos said:**
> I'm not familiar with Dell mini-10
Could you do a 

cat /proc/cpuinfo

and post the results?  

I've a Acer Aspire 1 netbook in the other room running without panic (so far) I'll post its results when I fire it up.

Thanks,

Jerry

As you asked, twin Atom:

frank@sweetie:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
stepping	: 2
microcode	: 0x211
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 xtpr pdcm movbe lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 2660.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
stepping	: 2
microcode	: 0x211
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 xtpr pdcm movbe lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 2659.96
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:
---

---

### Post by fjgaude on 2012-07-02
> **philinux said:**
> There is a new kernel in proposed. See sticky.

Thanks!

---

### Post by ronacc on 2012-07-02
I've been getting kernel panics on my amd64x2  box since 3.5.0-1 hit the repos  , both the not sync'ing and one about can't handle null pointer exception , has not occured yet on my box when running G-S , only unity . 

edit : spoke too soon chrome just precipitated a kernel panic while running G-S , when I tried to go to the bbc world news site .

---

### Post by philinux on 2012-07-03
3.5.0-3 just hit the main repos in my update today. Rebooted and running fine.

---

### Post by jerrylamos on 2012-07-03
Not familiar with Dell mini-10.  This is an Acer Aspire 1 10" netbook $250 at WallMart, 15.5" external monitor TV, wireless keyboard & mouse.  Nice.

Biggest trouble has been "No" automatic connection to wireless WPA network without a lot of slow manual going through systems settings netowrk on most boots:  Intel Corporation Centrino Wireless-N 1000

Just did today's 3.5.0-3  No panic.

It's a dual processor cat /proc/cpuinfo for one of them:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
stepping	: 10
cpu MHz		: 1666.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm
bogomips	: 3325.27
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

What's the cat/proc/cpuinfo for the Dell mini 10?

Jerry

---

### Post by fjgaude on 2012-07-03
Jerry, I posted the cpuinfo in #10 of this thread. The 10" Dell works perfectly with 12.04.

---

### Post by ventrical on 2012-07-03
I have an install of Quantal on my Acer Extensa 4420, dual core. I'll update and see whats up.

---

### Post by jerrylamos on 2012-07-06
Thanks, fjgaude, looks very similar to this netbook
Intel(R) Atom(TM) CPU N455   @ 1.66GHz dual processor too.

I'm doing O.K. with 3.5.0-3 except for very difficult to connect wireless WPA security, launchpad and upstream buges entered.

Jerry

---

### Post by fjgaude on 2012-07-06
I still get kernel panic with 3.5.0-3 when using the daily onto a USB flash. I'm good with 3.4 and earlier. I'll just wait it out, day-by-day. <smile>

---

### Post by lucazade on 2012-07-10
@fjgaude

[https://bitbucket.org/vincentliu/fc17-kernel-with-gma500-patches](https://bitbucket.org/vincentliu/fc17-kernel-with-gma500-patches)

" These are kernel sources for Fedora Core 17 (3.4+) with gma500_gfx patches for Linux-3.5"

these should fix our issues with kernel 3.5 and gma500_gfx, don't know if they will be included upstream in 3.5 release or not.

---

### Post by lucazade on 2012-07-10
@all
This issue is related only to Intel Atom Gma500.

Atom N455 and other chipset are really different so don't suffer of this issue.

---

### Post by fjgaude on 2012-07-10
> **lucazade said:**
> @fjgaude

[https://bitbucket.org/vincentliu/fc17-kernel-with-gma500-patches](https://bitbucket.org/vincentliu/fc17-kernel-with-gma500-patches)

" These are kernel sources for Fedora Core 17 (3.4+) with gma500_gfx patches for Linux-3.5"

these should fix our issues with kernel 3.5 and gma500_gfx, don't know if they will be included upstream in 3.5 release or not.

Thanks, Luca, for the tip. I'll just wait it out until Ubuntu 12.10 works, after all, 12.04 works just fine, better than anything so far. Not much interest until features are added over 12.04 to be excited. <smile>

---

### Post by htbw on 2012-07-10
I have a similar issue, at least that is one of the messages I get. This is my recent post with some sort of log attached. If anyone can help that would be awesome
[http://ubuntuforums.org/showthread.php?t=2022245](http://ubuntuforums.org/showthread.php?t=2022245)

---

### Post by lucazade on 2012-07-10
@htbw
different issue.. your ati radeon card has difficult to catch lcd panel edid.. edid is the "registry" of panel resolutions. open a bug report for this, it is a problem with radeon driver.
try also to upgrade bios.. sometimes edid is fixed that way.

here instead there is an issue with intel gma500 driver about panel brightness support via acpi.

---

### Post by konas on 2012-07-25
I also had kernel panics with all the versions of kernel 3.5 that I have tried, (3.4 is working fine) on my ACER 751H .
But fortunately the latest version 3.5.0.6 works without problem.

---

### Post by fjgaude on 2012-07-25
Yep, the last update, really ISO Alpha 3, did it. My Dell mini works like a charm. I'm sure Luca's machine does also. Even the brightness control works, wi-fi, etc. Thanks to Alan Cox and all the developers that have made this possible, gma500 lives!

---

### Post by lucazade on 2012-07-25
going to try.. tnx for heads up.
we can also try to use "modesetting" instead of fbdev.. i'll let u know ;)

---

### Post by fjgaude on 2012-07-28
Latest kernel update, 3.5.0-6, speeds the machine up, from about 40sec to 32sec, using **gtkperf**... that's a significant percentage.

On my main box, Intel i5-2405S, it went from 4.2 to 2.67sec. Now what goes on here with this updated kernel?

On either machine Suspend works but will not Resume.

---

### Post by lucazade on 2012-07-29
yep.. solved here as well :)

---

### Post by fjgaude on 2012-07-29
> **lucazade said:**
> yep.. solved here as well :)

Are you able to resume after suspend?

---

### Post by konas on 2012-07-29
> **fjgaude said:**
> Are you able to resume after suspend?

In my case it works without problems (Acer Aspire one 751h)
It s first time since ... long time ago ...

---

### Post by ronacc on 2012-07-29
A3 didn't do the trick for me ,it wouldn't even boot but the july 28 daily works like a charm on my AMD64 sys .

---

### Post by lucazade on 2012-07-31
> **fjgaude said:**
> Are you able to resume after suspend?

arg... even tried yet.. I use the netbook just in the spare time.
I still have to try:

* suspend and resume
* brightness hotkeys
* "modesetting" as driver in  [/etc/X11/xorg.conf]("http://pastebin.com/909sKXSU") ... it should work better than fbdev

---

### Post by fjgaude on 2012-07-31
With latest updates still will not resume... all else seems fine and has good speed.

---

### Post by ronacc on 2012-07-31
I'm back to my updated precise and the 3.4.0-5 kernel , 2 day old daily install wouldn't boot to dt without kernel panic and todays zsync'd amd64 wouldn't complete an install without panicking . oh well theres always 13.04 :lolflag:

---

### Post by fjgaude on 2012-07-31
> **ronacc said:**
> I'm back to my updated precise and the 3.4.0-5 kernel , 2 day old daily install wouldn't boot to dt without kernel panic and todays zsync'd amd64 wouldn't complete an install without panicking . oh well theres always 13.04 :lolflag:

My main box, notice signature, works perfectly with 12.10 latest updates. No issues, even resumes. But it's a different issue with the 32-bit Poulsbo Dell mini-10.

---

### Post by lucazade on 2012-08-08
> **lucazade said:**
> arg... even tried yet.. I use the netbook just in the spare time.
I still have to try:

* suspend and resume
* brightness hotkeys
* "modesetting" as driver in  [/etc/X11/xorg.conf]("http://pastebin.com/909sKXSU") ... it should work better than fbdev

ok.. tried modesetting as X driver.

You need to enable proposed repository, in order to upgrade to Xorg 1.13, and then install xserver-xorg-video-modesetting package.
At next reboot the brand new modesetting driver is enabled and loaded by default.. It is snappier than fbdev. Unfortunately no Vaapi and OpenGL extensions but who knows in  the future.

Btw I've enabled GPU-rendering in Chromium and I get a smooth scrolling... also Kde 4.9 is really fast :)

---

### Post by fjgaude on 2012-08-08
Thanks, Luca, for showing the way.

---

### Post by lucazade on 2012-08-08
further analisys:

* to get brightness hotkeys working on my acer I have to pass a parameter to kernel:
> acpi_backlight=vendor

* to get suspend working I have to remove default quirks database from suspend pm-utils
> sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video 


* using "modesetting" X driver glxgears goes up to 115fps (95 with fbdev)

* with "modesetting" external video output works correctly (tried with VGA, probably the same with HDMI)

* cpu usage seems lighter, probably because modesetting employs EXA as backend.

a step forward in the right direction, there is no need to do other tricks like in the past :)

---


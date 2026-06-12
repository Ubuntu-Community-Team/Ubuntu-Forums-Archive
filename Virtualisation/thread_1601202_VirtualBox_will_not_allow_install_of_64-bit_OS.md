---
title: "VirtualBox will not allow install of 64-bit OS"
date: 2010-10-19
forum: Virtualisation
---

### Post by scradock on 2010-10-19
I am running VBox in Ubuntu 10.10 64-bit; whenever I try to set up a 64-bit ubuntu guest I get a message that I have only a i686 system, so I have to install a 32-bit version instead.

To be more specific:after Loading initrd.gz.....ready    I get
"This kernel requires anx86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel apprpriate for your CPU."

My computer has an AMD64 cpu; Maverick is 64-bit through and through; VBox is the 64-bit version 3.2.10 r66523..........

I have tried the OSE version from the repo (3.2.8 ) and the PUEL version from Oracle (3.2.8 and 3.2.10, the latest), making sure to get the 64-bit version each time. Still the same error - it will only accept installation of 32-bit guests.

What am I doing wrong?

---

### Post by memilanuk on 2010-10-20
Sounds somewhat familiar...

Last summer I bought a brandy-new HP desktop, with 64-bit stickers all over the box.  It came running Windows Vista 64-bit, so I installed Virtualbox and tried installing the 64-bit version of Ubuntu, with similar results to what you got.

Turns out... just because there is a 64-bit cpu doesn't necessarily mean that the manufacturer turned on the extensions necessary for a 64-bit virtual machine.  In my case, HP apparently chose to cripple its consumer desktop models thus.

There might be an off chance that you may be able to turn on the virtual extension features in the bios, but you may be out of luck.

---

### Post by scradock on 2010-10-20
Thanks - the cpu runs 64-bit Ubuntu just fine, so it's not the same problem.

Oracle now claims that VBox can run 64-bit guests in a 32-bit host, with all the virtualization done in software - sounds like a miracle to me, but that's what they claim.

All I want to do is run a 64-bit guest in a 64-bit host - should be a simple enough thing to do - I'm sure lots of people here are doing it all the time.....

---

### Post by memilanuk on 2010-10-20
Maybe I didn't make myself clear... the crippled processors can run a 64-bit *host* OS just fine - doesn't matter if its Windows or Linux.  They lack the ability to run 64-bit *guests* - which is exactly what you're having problems with, same as I did.

---

### Post by scradock on 2010-10-20
Ah - that's interesting. I don't see any settings in the BIOS that relate to virtualization - did HP forget them too?

What properties do I look for in the cpu? and where do i find the list?

---

### Post by memilanuk on 2010-10-20
Yep.  I was somewhat less than pleased to find that myself.  Not enough to take the 'puter back, as I didn't really consider Virtualbox to be my primary use for it at the time, but maybe I should have.

I'm not sure if there is a test that can be run to verify if the cpu has the necessary extensions or not.  I'd imagine there is, I just don't know what it is.

BTW, I don't think you'll be able to run KVM either without those 64-bit virtualization bits either.

---

### Post by NightwishFan on 2010-10-20
You will most assuredly need hardware virtualization extensions (amd-vt, vt-x) to run Virtualbox with a 64-bit guest. Generally there should be a bios option to enable them.

Something like qemu can run a 64-bit guest without extensions I believe.

---

### Post by albandy on 2010-10-20
list the contents of /proc/cpuinfo and if in the section flags appears the vmx (virtualization extension) flag you can virtualize a 64 bit OS.

For example:
cat /proc/cpuinfo
[...]
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl **[COLOR="Red"][SIZE="5"]vmx[/SIZE][/COLOR]** est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid

---

### Post by scradock on 2010-10-20
Thanks, albandy. That was what I needed to check:

unfortunately it appears I'm screwed - no vmx flag set (very few, compared to yours, actually)

> flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up rep_good


Thanks, memilanuck - shame it isn't going to work. Well, the thing is 4-5 years old. Maybe time for a new one?

---

### Post by Quadunit404 on 2010-10-20
4 - 5 years old? Oh yeah, definitely. That's ancient in computing. Any older and your computer would be a dinosaur :lol:

If you want hardware-assisted virtualization, look for a computer with an AMD processor or one of the Intel processors [on this list]("http://www.tomshardware.com/news/windows-xp-mode-virtualization-intel,7709.html"). Amost all of AMD's processors ship with hardware-assisted virtualization support (the exception is the Sempron line - every other line ships with HAV support) and Intel ships select processors with HAV support.

Oh, and some brands such as Acer ship with HAV enabled by default, right down to some models not even allowing you to disable it in the BIOS (you don't *have* to use it in your virtualization app, with a few exceptions such as OS/2.) That's how virtualization-friendly some brands are :wink:

---

### Post by memilanuk on 2010-10-20
> Thanks, memilanuk - shame it isn't going to work. Well, the thing is 4-5 years old. Maybe time for a new one?

Well, if you are set on running 64-bit, probably so.  I seem to be able to run 32-bit pretty merrily for my uses, and probably will for years to come.  Still not entirely sure what attraction 64-bit has for a guest OS running on 2GB or less or RAM, etc?

---

### Post by scradock on 2010-10-21
> **memilanuk said:**
> Well, if you are set on running 64-bit, probably so.  I seem to be able to run 32-bit pretty merrily for my uses, and probably will for years to come.  Still not entirely sure what attraction 64-bit has for a guest OS running on 2GB or less or RAM, etc?
You're probably right - the machine is hopelessly underpowered for running several VMs simultaneously anyway; it just seemed ridiculous that it wouldn't even run one 64-bit OS as a guest.

The reason to run 64-bit guests is for simplicity; I have several 64-bit Ubuntu installs, but I wanted to play around with other variants, and it became too confusing having to have 32-bit install .isos for VM and 64-bit .isos for hosts.

By the way, as I have an AMD cpu the flag I need is apparently "svm", not "vmx". But I don't have that either, so that doesn't help. I wish I knew if there was a way I could alter the flags, rather than just reading them from cpuinfo.....

---


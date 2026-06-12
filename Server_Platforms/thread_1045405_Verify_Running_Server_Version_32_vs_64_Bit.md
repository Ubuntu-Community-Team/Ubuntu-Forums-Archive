---
title: "Verify Running Server Version: 32 vs 64 Bit"
date: 2009-01-20
forum: Server Platforms
---

### Post by california-ken on 2009-01-20
I&#7743; relatively new to Ubuntu so please be gentle.

I installed Ubuntu 8.04 Server, 64 bit with no problems.  Since the original installation, I have run ¨apt-get upgrade¨ a couple of times.

I now have new entries in my GRUB menu, one is identified as kernel 2.6.27-7-server and the other is identified as kernel 2.6.27-9-server.  GRUB points to the same disk partition for both but specifies different ¨initrd.img-2.6.27-x-server¨ files.

After the latest upgrade, my NVIDIA driver stopped working.  I downloaded the latest 64 bit driver for my NVIDIA card and when I tried to install it, it instantly produced a message that I was running a 32 bit version of Ubuntu.

1.  It appears that the apt-get upgrade process downgraded my server version from 64 bit to 32 bit.  Is there a place in Ubuntu I can determine explicitly if the 32 or 64 bit version is running?  I´ve checked the System Monitor and various log files.  They give the kernel version but don´t indicate if it´s a 32 or 64 bit kernel.

2.  If I have been downgraded to 32 bit, from a software and driver availability standpoint, should I take the trouble to reinstall Ubuntu Server 64 bit?  In the Windows world, there still are many software packages which will not run under Windows 64 and there is a real shortage of 64 bit drivers for hardware.  Does the same hold true for Ubuntu (or Linux in general)?

Thank you.

---

### Post by cdenley on 2009-01-20
I doubt your kernel was downgraded to 32-bit. Your system would have failed to boot, since all your binaries are 64-bit.
```

uname -m

```
Are you running the proprietary nvidia driver, or the open-source nv driver? The proprietary driver requires the restricted kernel modules. You can either install the restricted kernel modules for the server kernel (now and every time you upgrade the kernel), or simply install the desktop kernel.

to install the restricted modules for the server kernel you're currently running:
```

sudo apt-get install linux-restricted-modules-`uname -r`

```

to install the desktop kernel:
```

sudo apt-get install linux-generic

```
Open-source software has had great support for 64-bit platforms for years.

---

### Post by california-ken on 2009-01-20
Thank you for your prompt response.

1.  The response to the ¨uname -m¨ command was simply ¨i686¨.  No reference was made to 32 vs 64 bit.

2.  I&#7743; trying to run the latest proprietary NVIDIA driver from their web site.

3. I ran the ¨apt-get¨ commands you provided.  Now I have 6 choices in my GRUB menu.  There´s a mormal and recovery choice for 2.6.27-7 Server, 2.6.27-9 Generic and 2.6.27-9 Server.  

Should I have installed a package other then ¨linux-generic¨ for what you called the desktop kernel?

Depending on your response, I may take the plunge and reformat the partition and install server 64 bit.  I already downloaded the iso and burned it on a CD.  I&#7743; concerned that my Linux partition is getting too cluttered with various kernels, drivers, etc.

Thanks again.

---

### Post by cdenley on 2009-01-20
> **california-ken said:**
> Thank you for your prompt response.

1.  The response to the ¨uname -m¨ command was simply ¨i686¨.  No reference was made to 32 vs 64 bit.

2.  I&#7743; trying to run the latest proprietary NVIDIA driver from their web site.

3. I ran the ¨apt-get¨ commands you provided.  Now I have 6 choices in my GRUB menu.  There´s a mormal and recovery choice for 2.6.27-7 Server, 2.6.27-9 Generic and 2.6.27-9 Server.  

Should I have installed a package other then ¨linux-generic¨ for what you called the desktop kernel?

Depending on your response, I may take the plunge and reformat the partition and install server 64 bit.  I already downloaded the iso and burned it on a CD.  I&#7743; concerned that my Linux partition is getting too cluttered with various kernels, drivers, etc.

Thanks again.

i686 is 32-bit. If you were running 64-bit, the output would be "x86_64". You must have installed server 32-bit by accident. There is no way to switch which version you are running after the install. Also, there is no reason to download drivers from the manufacturer to get your devices to work properly. Ubuntu isn't windows.
-go to Applications>Add/Remove
-search for "nvidia"
-choose one of the 4 different versions available
-click "Apply Changes"
-Use the "desktop" or "generic" kernel.

---

### Post by cariboo on 2009-01-20
WHen running the server kernel it will also state that it is a server kerenl below is the output of uname -a :

```
 uname -a
Linux willy 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

```

Jim

---

### Post by gtdaqua on 2009-01-20
> **california-ken said:**
> I&#7743; relatively new to Ubuntu so please be gentle.

I installed Ubuntu 8.04 Server, 64 bit with no problems.  Since the original installation, I have run ¨apt-get upgrade¨ a couple of times.



To see if your hardware is capable of 64-bit, run "cat /proc/cpuinfo" in terminal and look for "lm" flag in the flags section. 'lm' means Long Mode supporting larger variables than the 32-bit does.

E.g. (modified output)
```

adminmaster:~$ cat /proc/cpuinfo
processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
<truncated....>
cpuid level	: 1
wp		: yes
**flags**		: fpu vme de pse tsc msr pae mce cx8 apic sep 
mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
syscall nx mmxext fxsr_opt rdtscp **[COLOR="Red"]lm[/COLOR]** 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

```

---


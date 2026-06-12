---
title: "Will there be a kernel 3.1 ?"
date: 2011-10-31
forum: The Cafe
---

### Post by Gremlinzzz on 2011-10-31
do you think they will upgrade the kernel?
Linux Kernel 3.1 Released, Adds Support for NFC Chips
Yes! After ten release candidates, Linus Torvalds marked a few minutes ago (October 24th) the Linux kernel 3.1 sources as final/stable and ready for immediate download.

Among the new features included in Linux kernel 3.1 we can mention OpenRISC opensource CPU support, various slab allocator improvements, writeback throttling improvements, new iSCSI implementation, Near-Field Communication chips support and Wii Controller support.

Linux kernel 3.1 provides better power management via the new cpupowerutils userspace utility, the EXT3 filesystem gets the filesystem barriers enabled by default, and lots of drivers were added and updated.

While there's no official announcement from Linus Torvalds, we can tell you that the new Linux kernel 3.1 brings improvements for the Intel Ivy Bridge chips, support for Cedar Trail, GMA500 enhancements, and much more.


[http://news.softpedia.com/news/Linux-Kernel-3-1-Released-Adds-Support-for-NFC-Chips-229562.shtml](http://news.softpedia.com/news/Linux-Kernel-3-1-Released-Adds-Support-for-NFC-Chips-229562.shtml)


I like the sound of this
Linux kernel 3.1 provides better power management

---

### Post by JDShu on 2011-10-31
Every new version of the kernel provides a wealth of features that weren't previously available. It's probably the fastest developing piece of software in the world.

---

### Post by juancarlospaco on 2011-10-31
Yes, it will be named Linux 3.11 for Workgroups.

---

### Post by pommie on 2011-10-31
> **juancarlospaco said:**
> Yes, it will be named Linux 3.11 for Workgroups.
Will you please pass me a towel to clean up the coffee on my keyboard and screen :P

Cheers David

---

### Post by cariboo on 2011-10-31
It's already here:

> uname -a
Linux Alexis-2 3.1.0-2-generic #3-Ubuntu SMP Sat Oct 29 00:48:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


Come help us test Precise.

---

### Post by Gremlinzzz on 2011-10-31
Just installed 3.1.0-2-generic #3-Ubuntu SMP Fri Oct 28 20:28:07 UTC 2011 i686 GNU/Linux
with 10.04
now to check it out with games:popcorn:

---

### Post by Gremlinzzz on 2011-10-31
kernels working fine, now i will upgrade my system:popcorn:

---

### Post by alphacrucis2 on 2011-10-31
> **juancarlospaco said:**
> Yes, it will be named Linux 3.11 for Workgroups.


New logo:

[IMG]http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/09/31-tuxlogo.png[/IMG]

---

### Post by ssam on 2011-11-01
> Once an Ubuntu release has been completed and published, updates for it are only released under certain circumstances, and must follow a special procedure called a "stable release update" or SRU. 
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

so ubuntu 11.10 will not get any major new version. The development version 12.04 already has kernel 3.1.

there are various ways to manually install kernel 3.1 into ubuntu 11.10, but you do so at your own risk. for example the ubuntu mainline kernel PPA, or compiling it your self.

---

### Post by Gremlinzzz on 2011-11-01
Spoke too soon;
kernel 3.1 is using 100% CPU in pogo games
going to remove it.:popcorn:

cant report that as a bug cause i was using 10.04
right?

---

### Post by philinux on 2011-11-01
> **ssam said:**
> [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

so ubuntu 11.10 will not get any major new version. The development version 12.04 already has kernel 3.1.

there are various ways to manually install kernel 3.1 into ubuntu 11.10, but you do so at your own risk. for example the ubuntu mainline kernel PPA, or compiling it your self.

The next kernel in proposed is 3.0.0-13.21

[http://status.qa.ubuntu.com/reports/kernel-bugs/reports/sru-report.html](http://status.qa.ubuntu.com/reports/kernel-bugs/reports/sru-report.html)

---

### Post by 3Miro on 2011-11-01
Ubuntu 12.04 will probably come with Linux 3.2. Older versions will not have official kernel upgrades, you can get unofficial ones, but then you cannot complain about bugs.

If you want to always keep up with the latest, you can pick a rolling release like Arch or Gentoo. The Ubuntu 6 months release cycle is as close as you can get to the latest software without sacrificing too much stability.

---

### Post by Gremlinzzz on 2011-11-01
The only kernel that is stable with my computer so far is
 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
comes with 10.04
might be my computer don't hear to many others complaining.
so i going to clean it good and check for anything loose:popcorn:

---

### Post by wman on 2011-11-01
I downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/,and](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/,and) have installed in several days~~but the vmware player didn't worked since that~

---

### Post by Gremlinzzz on 2011-11-01
> **Gremlinzzz said:**
> The only kernel that is stable with my computer so far is
 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux
comes with 10.04
might be my computer don't hear to many others complaining.
so i going to clean it good and check for anything loose:popcorn:

cleaning seems to have did it good 
going to check out unity on games:popcorn:


newer kernels not agreeing with my computer 
so ill use 10.04 till something changes

---

### Post by gregzeng on 2011-11-13
> **wman said:**
> I downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/,and](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/,and) have installed in several days~~but the vmware player didn't worked since that~

Interested if other virtual machines work ....

Looking forward to comparative benchmarks.  Using Xubuntu 11.10, cos Unity, Gnome3, ... are really alpha & beta releases IMO.

@JDShu 
"Every new version of the kernel provides a wealth of features that weren't previously available. It's probably the fastest developing piece of software in the world."

Every new software & hardware is either alpha or betaware.  History shows us this.  So - incompatibilities of all kinds, bugs, slow-downs of many types.

Retired CIO, Australian Capital Territory

---

### Post by bluexrider on 2011-11-13
> **alphacrucis2 said:**
> New logo:

[IMG]http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/09/31-tuxlogo.png[/IMG]

OMG rotflmaf..........Thats not good, thats classic!

---

### Post by LowSky on 2011-11-14
Im using Kernel 3.1.0-4 right now. Seems to work great.

---

### Post by Gremlinzzz on 2011-11-14
I'm using
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
working great computer is running cool.:popcorn:

---

### Post by MG&amp;TL on 2011-11-14
When's the power management meant to be improving? As in, what kernel release.

---

### Post by Gremlinzzz on 2011-11-14
Not sure.
Got my improvement by installing 
Linux Mint 12 'Lisa' RC
 the 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

is the OS's default kernel:popcorn:

---

### Post by MG&amp;TL on 2011-11-14
Hmmmm.that's my version or similiar. Ubuntu 11.10, still running quite hot, 2 hours or so battery life, 4 on Windows. :(

Might have to compile my own, see what happens. Or get it from the PPA.

---


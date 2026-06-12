---
title: "Win vs Ubuntu"
date: 2013-08-29
forum: Ubuntu, Linux and OS Chat
---

### Post by czgirb on 2013-08-29
While using **Windows**, we often heard a statement, which say "**the more application installed, the slower the CPU will become**"
Is the **rule remains to be valid** also in **Ubuntu**?
Please guide me ...

---

### Post by carl4926 on 2013-08-29
How many applications are 'Installed' should not make any difference.
It's if they are in use that matters.
Of course windows software does have a habit of being loaded in to the system tray or some such area

---

### Post by mastablasta on 2013-08-29
> **czgirb said:**
> While using **Windows**, we often heard a statement, which say "**the more application installed, the slower the CPU will become**"


not true. 

windows NTFS file system has high fragmentation rate. so the more data you put on and then delete, the higher the fragmentation. high fragmentation slows down the disk and so the system itself.

linux uses other file systems (defualt in UButnu is ext4) which doesn't have such a high framentation. so disks are at about same speed all the time.

if you defragment the drive in windows the system should be responsive.

regarding disk speed on classic disks - it does matter (no matter what is on disk - OS or if it's only data) how much the disk is full.

---

### Post by rai_shu2 on 2013-08-29
I wouldn't dismiss such claims. It does, however, depend on your hardware. Let's say your hard drive has 32 MBs of cache on it. The more applications you have, the more icons and other info on those applications have to be accessed for the desktop to function properly. This is true for both Windows and Ubuntu (as far as I understand it), so your best bet would be to have just the right amount of disk usage to fill the cache without needing it to flush frequently. With 32 MBs or more, I think you'd be unlikely to see that cache filled too terribly frequently, but that depends on how you use it.

The thing I'm thinking is that systems that run fast are the ones that make the best use of the caches provided. That's always been my experience. I suppose it's possible to have too many applications, although that becomes less and less true every year with these new monster hardware manufacturers keep making.

---

### Post by prodigy_ on 2013-08-29
> **czgirb said:**
> **the more application installed, the slower the CPU will become**
First, CPU is hardware that can only become "slower" when something limits its frequency (e.g. Intel SpeedStep energy saving tech).

Second, Windows uses so-called registry database to store a large amount of settings. Some registry keys store system settings others store application settings. For various reasons (e.g. uninstallers leaving unnecessary keys behind) registry tends to grow over time. And looking something up in a larger database is always slower. Cleaning up registry is possible but it can be quite tricky and any "cleaner" utilities should be used carefully.

Third, as already mentioned, for HDDs file system fragmentation can result in heavy performance degradation of all disk I/O (starting programs, reading/writing data, etc) operations. Defragmentation usually helps. Conversely, SSDs are much less impacted by fragmentation but they require TRIM to be enabled for optimal performance and their performance always gradually degrades over time due to physical wear.

Fourth, many Windows applications are bloatware. They install unnecessary services and startup "helper" apps that consume resources while rarely being useful. Unnecessary services and startup items need to be disabled manually (e.g. with **msconfig** tool).

---

Linux doesn't have registry and its native file systems are less susceptible to fragmentation but, for instance, SSD wear will have the same effect on I/O performance.

Long story short: with proper maintenance performance degradation will be almost negligible even in Windows.

---

### Post by buzzingrobot on 2013-08-29
Installing software has zero impact on the CPU.

Actually loading and running software puts demands on the CPU, but, by itself, has no impact on CPU speed. The CPU gets busier as more software runs.  (I'd guess few Windows users clean out unnecessary startup apps and services.  Ditto for a suprising number of Linux users, probably.)

Disk operations can slow as drives fill.

Any OS that finds itself swapping frequently will be noticed by users.  But, that's not a CPU issue.

---

### Post by dusanyu on 2013-08-29
this can be true in one case Swap space or as windows calls it "Virtual memory" Windows Systems have always used a portion of unused space on its root directory for swap this can be over written and or taken over by data so, under windows it is possible to fill your drive that it can no longer use swap space. GNU/Liunx and other POSIX Like operating systems use the older method of using a separate drive or partition for swap space, protecting that drive space form being written into by data.


While swap is a non issue these days with 8 Gigabytes or more of core memory these days. it used to be witch is the origin of the belief that windows gets slower when the drive gets full

for more information see 
[http://windows.microsoft.com/en-us/windows-vista/what-is-virtual-memory](http://windows.microsoft.com/en-us/windows-vista/what-is-virtual-memory)

---

### Post by buzzingrobot on 2013-09-01
If you try to load X+1 into memory of size X, the OS will swap, no matter how much physical memory it has. While many people never get to X+1, that doesn't mean swapping is no longer needed. 

Disk space is a separate issue and wasn't linked to any particular OS. Time to write data depends, in part, on the unused capacity of the disk, the size of the unused bits, and their location.

---


---
title: "xfs or ext4 etc.?"
date: 2012-06-02
forum: Server Platforms
---

### Post by ahso4271 on 2012-06-02
Hi
i remarked ext4, after a power failure, often needs a manual fsck, sometimes even resulting in data loss. Is XFS or other filesystems any better? Can I do fsck with xfs from the rescue boot etc.?
Thanks

---

### Post by Gyokuro on 2012-06-02
Hi

There are opinions about that xfs is more vulnerable to power outages then ext4 . However in practice I can only say it is vice versa - ext4 is much better in this matter (took the power plug during writes, ext4 fscked and was fine afterwards and xfs was dead). You should do something against your power outages.

---

### Post by rubylaser on 2012-06-02
> **Gyokuro said:**
> Hi

There are opinions about that xfs is more vulnerable to power outages then ext4 . However in practice I can only say it is vice versa - ext4 is much better in this matter (took the power plug during writes, ext4 fscked and was fine afterwards and xfs was dead). You should do something against your power outages.

+1 I avoid XFS like the plague after numerous problems over the years.  Most not even power related.  The first step should be getting a UPS and setting it up properly. With a proper UPS, ext4 is VERY stable.

---

### Post by ahso4271 on 2012-06-11
ZFS seems the best but not available on Ubuntu? Why is that included in FreeBSD but not on Ubuntu? Ubuntu could create some button "install not gpl software" alike for Flash etc.?

What about the other FS alike JS?

Ext4 should get better with kernel 3.5 and later?

---

### Post by idoitprone on 2012-06-11
> **ahso4271 said:**
> ZFS seems the best but not available on Ubuntu? Why is that included in FreeBSD but not on Ubuntu? Ubuntu could create some button "install not gpl software" alike for Flash etc.?

What about the other FS alike JS?

Ext4 should get better with kernel 3.5 and later?

Dont use ZFS. It was conceived by Sun Microsystems for Solarisn not linux. It uses CDDL license which is not compatible with stallmans GPL.  Those new and advance filesystems have features that will never appear on the desktop. I believe ZFS is a future proof for 128 bit computers, which will not exist for at least half a decade. Use a supported file system like ext4. Both ext4, ZFS, XFS have comparable performance.

I would tell you to be wary of experimental filesystems, because data recovery is not easy. Besides,  XFS only recently solve their meta data problem. ZFS is still considered new, and Brts have some problems.

Just use ext4 because it is both fast and stable.

I believe ext4 wont get much faster, but it  only got slightly faster in kernel 3.4 because it is reading with larger blocks, i believe.

---

### Post by ahso4271 on 2012-06-11
I'm not talking about speed but reliability.-

On 12.04 64bit I often end with a crash. Not even recover boot is able to do a fsck!- Luckily I still have 10.04 32bit aside to do a fsck.
On 10.04 32bit I never had such...feels like a prehistoric linux...sigh.

---

### Post by rubylaser on 2012-06-11
> **ahso4271 said:**
> I'm not talking about speed but reliability.-

On 12.04 64bit I often end with a crash. Not even recover boot is able to do a fsck!- Luckily I still have 10.04 32bit aside to do a fsck.
On 10.04 32bit I never had such...feels like a prehistoric linux...sigh.

[zfsonlinux]("http://zfsonlinux.org/") is pretty good at this point and runs natively on Ubuntu at this point.  But, if you want to use ZFS, I'd still push you to use Solaris/Openindiana/Nexenta at this point because they're all proven implementations of ZFS.

What makes 10.04 seem prehistoric?  Are you taking about the server version or desktop?

In regards to 12.04, have you looked at the log files to try to figure out what's causing the crash? Consistent crashes should not be happening on what's considered a stable OS.

---

### Post by idoitprone on 2012-06-11
> **ahso4271 said:**
> I'm not talking about speed but reliability.-

On 12.04 64bit I often end with a crash. Not even recover boot is able to do a fsck!- Luckily I still have 10.04 32bit aside to do a fsck.
On 10.04 32bit I never had such...feels like a prehistoric linux...sigh.

12.04 crashing is because of Ubuntu's fault. The shift in resources in making Unity stable have caused the distro to be unstable.

Change distros like Opensuse or debian to get something more stable

---

### Post by Cheesemill on 2012-06-11
> **idoitprone said:**
> 12.04 crashing is because of Ubuntu's fault. The shift in resources in making Unity stable have caused the distro to be unstable.

Change distros like Opensuse or debian to get something more stable
Maybe for you, I've found 12.04 to be rock solid on all of the desktops and servers that I've installed it on.

---

### Post by idoitprone on 2012-06-11
> **Cheesemill said:**
> Maybe for you, I've found 12.04 to be rock solid on all of the desktops and servers that I've installed it on.

I like to blame on things that is more likely. Canonical breaking Ubuntu is hundred times more likely than ext4 causing the crash. With harddrives, it is mostly hardware failure rather than a stable tested linux filesystem that is most likely to mess up

---

### Post by ahso4271 on 2012-06-13
Two days ago I had firefox and opera open as 12.04 crashed. I couldn't even 
do a fsck in recovery boot but had to go 10.04 for fsck and be able to reboot 12.04.

FreeBSD uses ZFS? So why the heck can they use it, but not on Linux? It would 
be neat to be able to use zfs on the next ubuntu or so. I mean easy, not as on Sabayon.

---

### Post by rubylaser on 2012-06-13
You can use ZFS on linux.  It's available via [zfsonlinux]("http://zfsonlinux.org/"), but it's not yet considered stable or tuned for performance, but they are actively developing it, and it works fairly well in my own testing.

---

### Post by arrrghhh on 2012-06-13
> **ahso4271 said:**
> Two days ago I had firefox and opera open as 12.04 crashed. I couldn't even 
do a fsck in recovery boot but had to go 10.04 for fsck and be able to reboot 12.04.

FreeBSD uses ZFS? So why the heck can they use it, but not on Linux? It would 
be neat to be able to use zfs on the next ubuntu or so. I mean easy, not as on Sabayon.

Why are you running Firefox or Opera on a server...?

I find ext4 very stable.  It's been running for a couple of years now on my server... No crashes/blips/etc to speak of.  Just solid.

---

### Post by rubylaser on 2012-06-13
> **arrrghhh said:**
> Why are you running Firefox or Opera on a server...?

I find ext4 very stable.  It's been running for a couple of years now on my server... No crashes/blips/etc to speak of.  Just solid.

+1. ext4 is rock solid and I use it on all of my home boxes and servers at work where the filesystem size is < 16TB.  The only time I've ever had to fsck one of my boxes was during a work power outage and one of our old UPS's died in about 10 seconds (bad battery) before the generator kicked on.

---

### Post by ratcheer on 2012-06-13
I believe, from all I have read, that xfs is somewhat faster, but ext4 is much more reliable. In my own experience, ext4 has been "rock solid". However, I will disclose that I have never used xfs.

Tim

---

### Post by nw68868 on 2012-09-15
Personally I really Like XFS. I use it on both my main server and My home laptop.

For my server, the main data partition is in XFS.

For my laptop, The home partition is in XFS

In both of these situations, the file-system is being used to store large files and in both systems the computer is protected by a UPC ( or battery) I have never had a problem, even with HARD reboots.

Even across several HARD HARD reboots and across multiple re-installs I have never had a problem. I always recommend XFS for read intensive, write minimal applications.

---

### Post by thnewguy on 2012-09-15
ext3 and ext4 are about as solid as file systems get, at least on Linux. If you're experiencing power outages or crashes then you should definitely be using one of these. Of course, the best protection against data loss is regular backups, regardless of what file system you use. Hardware failure will make your file system pretty irrelevant.

The reason most distributions don't ship with ZFS is because of the license. The Linux kernel's license (GPL) is not compatible with the ZFS license (CDDL). This means ZFS is only available as an add-on. FreeBSD is able to ship with ZFS because they have a less restrictive license.

I use ZFS on my Ubuntu home server and it has been pretty good. The only issue I had was during an upgrade of ZFS packages, which caused some corruption. ZFS was able to recover and keep working.

---

### Post by sandyd on 2012-09-15
If your looking for reliability, I suggest JFS. It recovers fast, and can take a lot of damage while making sure your files are not corrupted. That is, if you have less memory. If you have enough memory for performance, go with ZFS. They recently fixed the preempt bug, so it is safe to install on linux servers. If you are worried about crashes, install a BBU unit to your drives.

I use XFS only because it transfers fast, and its on a RAID6 array so not much chance for corruption/crashes. Drives have BBUs installed, along with a UPS and datacenter backup generators.

---

### Post by TenPlus1 on 2012-09-16
I would recommend purchasing a UPS for your computer so that the power wont go down during an outage and damage your hard-drive at all, as well as any other pieces of equipment you have connected to your system...

---


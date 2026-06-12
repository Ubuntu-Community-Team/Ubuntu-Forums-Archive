---
title: "AVG in 64bit - false positive?"
date: 2009-02-10
forum: Security
---

### Post by jso2897 on 2009-02-10
I just recently installed AVG 7.5 for Linux on my 64bit Ubuntu boxes - and it comes up positive, identifying a couple of .ko files in the SCSI driver folders in the kernels. These files are part of the kernel install itself, are not deleteable, and can't possibly be malware of any kind. Anybody have any idea what gives here? Never happened on any of my 32 bit installs. I wonder if it's because I had to force the dpkg install to get it to install in 64 bit.
Any ideas?:confused:

---

### Post by jso2897 on 2009-02-10
OK, so I went and updated and ran AVG on one of my 32bit boxes - no positive. And the same kernel files (or at least their equivalents, with the same names) exist in the 32bit kernels. So apparently, forcing the i386 version of AVG 7.5 to dpkg in 64bit causes this.
I hate computers.
:(

---

### Post by hyper_ch on 2009-02-11
why do you use antivirus to scan your linux installation?

---

### Post by jso2897 on 2009-02-11
> **hyper_ch said:**
> why do you use antivirus to scan your linux installation?

Oh, no good reason really - it's a free app, and it's fun to fool around with. And on the serious side, I always have at least one dual boot machine going, and if you have a Windows partition that gets badly befargled by some sort of nastiness you pick up somewhere, it's really useful to be able to scan it for malware from the safety of your Linux partition. But in 3 years of running AVG on my Linux installs, these false positives are the only hits I've ever gotten (on a linux partition). I did once use it to remove a rootkit from a Windows partition that wouldn't boot. Darn handy.

---

### Post by hyper_ch on 2009-02-12
but still, why do you scan your linux installation with it and not just the files you probably share accross?

---


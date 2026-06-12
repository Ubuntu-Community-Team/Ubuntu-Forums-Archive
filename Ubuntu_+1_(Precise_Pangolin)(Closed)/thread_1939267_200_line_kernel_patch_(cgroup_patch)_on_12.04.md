---
title: "200 line kernel patch (cgroup_patch) on 12.04?"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by synaptix on 2012-03-11
Is anyone using the [cgroup_patch]("http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html") on their 12.04 install and notice any difference?

---

### Post by dino99 on 2012-03-11
hm, a patch from 2010 ? a bunch of new kernels have been published since that time :)
If you are looking your kernel log, you will see some comments about it, and what to do if you are concerned.

---

### Post by synaptix on 2012-03-11
> **dino99 said:**
> hm, a patch from 2010 ? a bunch of new kernels have been published since that time :)

I am aware, but the patch supposedly works on 11.10 too with that kernel version. Just wondered if anyone had it running on their 12.04 install and can confirm it working before I try it?

---

### Post by tista on 2012-03-11
You mean the "miracle patch"?

In that time, I've tried it out onn 2.6.3x kernel, But this patch might not be suitable for average-users, isn't it?

Because cgrouping makes some effects of avoiding "resource drain" between console ttyA and graphical ttyB. if so, it would be welcome to developers desktops. Yep, they usually run X while building were continued on background as another tty or so...

I don't think this patch could be needed by everyone... ;)

Regards,
Tista

---

### Post by synaptix on 2012-03-11
> **tista said:**
> ...

It worked wonders on my 10.04 install @ 2.6.32 kernel, but I just recently installed 12.04 and hoping to see if anyone else running it against 3.2.0 kernel with success and results.

---

### Post by manzdagratiano on 2012-03-11
Wasn't the 'miracle patch' merged in the mainline Linux kernel since 2.6.38?

---

### Post by Sworddragon on 2012-03-11
> **manzdagratiano said:**
> Wasn't the 'miracle patch' merged in the mainline Linux kernel since 2.6.38?

This is correct and this was the only patch that made a huge performance difference on my system. Before 2.6.38 I got freezes of some minutes if something was written to my hard disk drive. After this patch all is running fine. But there is still a "bug" on journaling operations. If you nice a process with ionice the journaling process doesn't prioritize the write operations to the same level.

---

### Post by synaptix on 2012-03-11
> **manzdagratiano said:**
> Wasn't the 'miracle patch' merged in the mainline Linux kernel since 2.6.38?

Not sure, since the 'miracle patch' still works against Ubuntu 11.10 which runs kernel 3.0.

---

### Post by dcstar on 2012-03-12
12.04 already has the **cgroup.lite** package to set up use of cgroups.

---

### Post by manzdagratiano on 2012-03-12
> **synaptix said:**
> Not sure, since the 'miracle patch' still works against Ubuntu 11.10 which runs kernel 3.0.

Hmmm... That is weird. In particular, take a look at

[kernel.org/doc/ols/2011/ols2011-masters.pdf]("http://kernel.org/doc/ols/2011/ols2011-masters.pdf")

in which there is a chronological slide that states the patch was posted to 2.6.38-rc7. There is probably a corresponding post at lkml.org, but that might need to be dug up. I am ATM also interested in looking up stuff regarding the BFS scheduler and why it is unlikely it will ever be merged into the mainline kernel. [s]Maybe it should be made into a package?[/s]

---

### Post by synaptix on 2012-03-12
> **manzdagratiano said:**
> ...

I got curious last night and decided to run the patch against my current 12.04 install on kernel 3.2.0, and the patch has increased the performance of my system once again.

Really weird. :S

---

### Post by tekstr1der on 2012-03-12
> **synaptix said:**
> Is anyone using the [cgroup_patch]("http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html") on their 12.04 install and notice any difference?

Yes, everyone on a 2.6.38+ kernel has the patch including all natty, oneiric and 12.04 users.

As others have stated this was merged in 2.6.38 RC1. See Linus comments on LKML:
[https://lkml.org/lkml/2011/1/18/322](https://lkml.org/lkml/2011/1/18/322)

Here's a link to the git commit:
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=5091faa449ee0b7d73bc296a93bca9540fc51d0a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=5091faa449ee0b7d73bc296a93bca9540fc51d0a)

---

### Post by dcstar on 2012-03-13
> **synaptix said:**
> I got curious last night and decided to run the patch against my current 12.04 install on kernel 3.2.0, and the patch has increased the performance of my system once again.


And did you install any of the 12.04 packages that actually set up the use of cgroups?

---

### Post by screaminj3sus on 2012-03-13
> **synaptix said:**
> I got curious last night and decided to run the patch against my current 12.04 install on kernel 3.2.0, and the patch has increased the performance of my system once again.

Really weird. :S

I must say, this looks like "placebo effect" to me lol..

---

### Post by dcstar on 2012-03-15
> **screaminj3sus said:**
> I must say, this looks like "placebo effect" to me lol..

No, part of the "patch" is actually setting up the cgroup structures manually - specifically a CPU Control Group - so doing that may simply just turn on the inherent cgroup functionality that is already in the kernel.

As I have posted previously, 12.04 now has cgroup packages that AFAIK **have to be installed to set up to use cgroup features**, and until the OP actually does this then his/her "test" is worthless.

Using cgroups can have a major performance impact on systems that have certain hardware setups, specifically in maintaining system response while simultaneously copying large amounts of data which keeps the disks 100% busy.

---


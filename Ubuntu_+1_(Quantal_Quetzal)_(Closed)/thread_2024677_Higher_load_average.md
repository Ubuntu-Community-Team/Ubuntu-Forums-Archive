---
title: "Higher load average"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by paul_in_london on 2012-07-14
I noticed a while back (at some point during the precise dev cycle) that the load I saw via htop seemed to be much higher than it had been, but I couldn't remember when it happened and I wasn't sure if it was just something to do with my own setup or aging hardware. (I use byobu anway so I always have an idea of the general load without using htop).

Anyway it apparently kicked in somewhere around kernel 3.2.0-21. With kernel 3.2.0-21 the load was still "normal" according to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)

So as a test I installed this kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-precise/)

and the load is now (at least reported as) more sane.

```
paul@quantal-64:~$ uname -a
Linux quantal-64 3.2.0-030200-generic #201201042035 SMP Thu Jan 5 01:36:31 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@quantal-64:~$ 
```

According to post #78 in the bug report, kernel 3.5-rc7 will include a patch to fix the issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661/comments/78](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661/comments/78)

---

### Post by QIII on 2012-07-14
Seems a bit of a moot point?

```
wouldntyouliketoknow@Ubuntu-Quantal:~$ uname -a
Linux Ubuntu-Quantal 3.5.0-4-generic #4-Ubuntu SMP Mon Jul 9 22:31:58 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by paul_in_london on 2012-07-16
Not seeing much change here with 3.5-rc7 despite what Doug Smythies says here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661/comments/80](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661/comments/80)

Related launchpad bugs:

[https://bugs.launchpad.net/ubuntu/+bug/993007](https://bugs.launchpad.net/ubuntu/+bug/993007) (duplicate)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811)

Found this (by Doug), which is quite interesting:

[http://www.smythies.com/~doug/network/load_average/new.html](http://www.smythies.com/~doug/network/load_average/new.html)

EDIT: It's mentioned in here actually:

[https://www.networkworld.com/news/2012/071612-linux-rc7-torvalds-260919.html](https://www.networkworld.com/news/2012/071612-linux-rc7-torvalds-260919.html)

---

### Post by Doug S on 2012-07-17
> **paul_in_london said:**
> Not seeing much change here with 3.5-rc7 despite what Doug Smythies says here:If you run Ubuntu DeskTop edition, I would have expected you to have a noticably different reported load average, lower, when your computer is more or less idle. I only run ubuntu server edition, so I had to simulate the problematic conditions.

---

### Post by paul_in_london on 2012-07-17
> **Doug S said:**
> If you run Ubuntu DeskTop edition, I would have expected you to have a noticably different reported load average, lower, when your computer is more or less idle. I only run ubuntu server edition, so I had to simulate the problematic conditions.

Hi Doug,

Thanks for your response. This is a minimal gnome setup (derived from a boot-only image in one of the earlier dev cycles - Natty or Oneiric I can't quite remember now).

The load averages reported by the **3.5-rc7** kernel do seem a little lower now under the same conditions, but still significantly higher than I'd been used to seeing with earlier kernels (e.g. **3.2.0-030200-generic**).

However when I tested the other day using **3.2.0-030200-generic** I was unaware that the reported load averages were apparently too low prior to the release of **3.4RC1**:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811/comments/49](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/838811/comments/49)

so obviously that complicates the issue.

Cheers,

Paul

---


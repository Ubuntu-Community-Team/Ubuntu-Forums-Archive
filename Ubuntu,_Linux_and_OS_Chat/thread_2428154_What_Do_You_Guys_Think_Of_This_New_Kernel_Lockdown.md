---
title: "What Do You Guys Think Of This New Kernel Lockdown Feature?"
date: 2019-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by DeadlyOats on 2019-09-30
There's a new feature that will be coming out on future versions of [the Linux Kernel]("https://www.zdnet.com/article/linux-to-get-kernel-lockdown-feature/?ftag=TRE-03-10aaa6b&bhid=23586413726101147691015284598822").  What do you guys think of it?

---

### Post by #&amp;thj^% on 2019-09-30
The new feature will ship as a LSM (Linux Security Module) in the soon-to-be-released Linux kernel 5.4 branch, where it will be turned off by default; usage being optional due to the risk of breaking existing systems.
As I understand it, The new feature's primary function will be to strengthen the divide between userland processes and kernel code by preventing even the root account from interacting with kernel code -- something that it's been able to do, by design, until now.
As with all new kernel mods, I watch with curiosity. [https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-Kernel-Lockdown-PR](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.4-Kernel-Lockdown-PR)
Good read: [https://lwn.net/ml/linux-kernel/20190326182742.16950-1-matthewgarrett@google.com/](https://lwn.net/ml/linux-kernel/20190326182742.16950-1-matthewgarrett@google.com/)

---

### Post by DeadlyOats on 2019-09-30
Phoronix gave a real good summary of what it could do.  Would something like this help, for example, to prevent those incredible banking cracks that get millions of people's account information stolen?  Or what kind of threat exactly is the lockdown feature designed for?

The one thing I'm glad about is that it is off by default.  I don't know that I would be able to configure my hardware to run properly if Linux prevented stuff from accessing the hardware to do stuff...  if that lockdown was on by default...

As you can see, I am not a very technical end user, but at least I can see a potential for trouble for non-technical guys like me to build my own PC's and install my own operating systems if things that are beyond my technical abilities were locked down....

---

### Post by #&amp;thj^% on 2019-09-30
In my short tests, the goal of the lockdown mode is to prevent someone who has UID=0 ("root") in the kernel from being able to modify or tamper with it (ring0 / CPL0 access). This can be done through /dev/mem, kexec, or even by asking a PCI card or FireWire device to DMA into physical system memory. Basically, there are a lot of hooks to tamper with the kernel, and "lockdown" mode turns them off. (In a nut-shell)

---

### Post by cruzer001 on 2019-09-30
This sounds like a feature geared more towards production machines.  As just a home user I wonder if the extra security will be useful.

---

### Post by #&amp;thj^% on 2019-09-30
Why in the world wouldn't it be useful?
And- production, hobbyist, home/user, added security is always welcome. (At least here it is :))
Do you access banks?
Take what I say with a grain of salt, I monitor networks, and see things that would raise the hair on the back of your neck. :o
And a old saying that goes like: "Failing to Plan is Planing to Fail"
I think I understand your concerns, but it will be a configurable change;
> "none" results in no behavioural change, "integrity"
enables features that prevent untrusted code from being run in ring 0,
and "confidentiality" is a superset of "integrity" that also disables
features that may be used to extract secret information from the kernel
at runtime. 

---

### Post by Skaperen on 2019-09-30
> **cruzer001 said:**
> This sounds like a feature geared more towards production machines.  As just a home user I wonder if the extra security will be useful.
it depends if you are interesting as a target.   you might be, some day, if not already.  as i am building production tools, i am, at least a bit.

---

### Post by Skaperen on 2019-09-30
> **1fallen said:**
> Do you access banks?
no!

---

### Post by cruzer001 on 2019-09-30
> "none" results in no behavioural change, "integrity"
enables features that prevent untrusted code from being run in ring 0,
and "confidentiality" is a superset of "integrity" that also disables
features that may be used to extract secret information from the kernel
at runtime.
Ok,that got my attention

Guess we will see this in 20.04

---

### Post by Skaperen on 2019-09-30
> **cruzer001 said:**
> Ok,that got my attention

what mode will you set your kernel to?

> **cruzer001 said:**
> Guess we will see this in 20.04

i'm looking forward to shaking out more poorly designed hacks of softwarez.

---


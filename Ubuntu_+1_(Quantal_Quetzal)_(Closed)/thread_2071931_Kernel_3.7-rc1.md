---
title: "Kernel 3.7-rc1"
date: 2012-10-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Rukiri on 2012-10-16
Anyone try 3.7 rc1 yet? Just installing a base gentoo system with btrfs to see how to goes, many new options and many menus have changes but most are the same.

Looks like they FINALLY added support for the saitek mice maybe I won't have to edit the xorg.conf file anymore?  Hope my new das keyboard works(arrives today)

I really don't like compiling the kernel, know how but the process is..well long.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
it still lacks the all.deb in mainline
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc1-quantal/)

---

### Post by Rukiri on 2012-10-16
doesn't ubuntu wait til the kernel matures before it add it to the repos?  You could always download and compile from source no reason to use ubuntu specific kernels.

---

### Post by Milos_SD on 2012-10-16
I compiled it, and added some new options about IRQ, memory hot-add, etc ... And now, when my browser is loading pages, I get a almost 100% iowait and a lot of disk read activity from home partition. Don't know why is that happening. :S

---

### Post by Rukiri on 2012-10-16
What terminal commands are you using?

---

### Post by Milos_SD on 2012-10-17
Well, the standard for debian/ubuntu:

```

cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
```

```
make xconfig
```
Here I make some changes to the config if I want to. 
Then:

```
make-kpkg clean
```

```
CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

When this step is finished, I have 2 .deb files, image and headers. I install them and reboot my pc. :)

---

### Post by zika on 2012-10-17
> **Milos_SD said:**
> Well, the standard for debian/ubuntu:

```

cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
``````
make xconfig
```Here I make some changes to the config if I want to. 
Then:

```
make-kpkg clean
``````
CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```When this step is finished, I have 2 .deb files, image and headers. I install them and reboot my pc. :)We already highjacked 3.6 thread [http://ubuntuforums.org/showthread.php?p=12300339#post12300339](http://ubuntuforums.org/showthread.php?p=12300339#post12300339) talking about 3.7, post #38 and on... You are, also, mentioned... ;)
@ Milos_SD: Even though with &#8222;crippled&#8220; kernel I'm not seeing anomalies You mention...

---

### Post by funicorn on 2012-10-17
No. One has good reasons to use ubuntu specific kernel if he runs ubuntu.
> **Rukiri said:**
> doesn't ubuntu wait til the kernel matures before it add it to the repos?  You could always download and compile from source no reason to use ubuntu specific kernels.

---

### Post by JMB74 on 2012-10-17
Also may interest some:

[https://lists.ubuntu.com/archives/kernel-team/2012-October/022464.html](https://lists.ubuntu.com/archives/kernel-team/2012-October/022464.html)

---

### Post by Milos_SD on 2012-10-17
I fixed the issue by using this settings in "CPU/Task time and stats accounting"

```
CONFIG_TICK_CPU_ACCOUNTING=y
# CONFIG_IRQ_TIME_ACCOUNTING is not set
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
CONFIG_TASK_DELAY_ACCT=y
# CONFIG_TASK_XACCT is not set
```

Before I had "CONFIG_TASK_XACCT" and "CONFIG_IRQ_TIME_ACCOUNTING" enabled.

@zika: You didn't compile the kernel. And I bet this options are not enabled in mainline kernel. :)

---

### Post by zika on 2012-10-18
> **Milos_SD said:**
> I fixed the issue by using this settings in "CPU/Task time and stats accounting"

```
CONFIG_TICK_CPU_ACCOUNTING=y
# CONFIG_IRQ_TIME_ACCOUNTING is not set
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
CONFIG_TASK_DELAY_ACCT=y
# CONFIG_TASK_XACCT is not set
```Before I had "CONFIG_TASK_XACCT" and "CONFIG_IRQ_TIME_ACCOUNTING" enabled.

@zika: You didn't compile the kernel. And I bet this options are not enabled in mainline kernel. :)Of course I did not. I had a premature and sudden death of my modem/router, replaced it with spare one and lost that little of spare time that I saved for compiling. Next time... ;) Maybe today, maybe tomorrow... Who knows... The answer my friend is blowing with the wind...
As always, if i do compile I will use Your settings... Thank You.. ;)

---


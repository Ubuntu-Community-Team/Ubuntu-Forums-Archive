---
title: "Testing New kernel versions"
date: 2015-07-01
forum: Ubuntu Development Version
---

### Post by lyf on 2015-07-01
Hi Experts,

During each of the kernel release like 4.1, how to test the functionality of the kernel or experiment it ?

I am able to download the source but how to evaluate it ?

---

### Post by Bucky Ball on 2015-07-01
*Thread moved to **Ubuntu Development Version**.*

You'll get more help here if you're wanting to test unreleased, unstable kernels and the upcoming OS Wily Werewolf (I believe the 4.1 kernel will be included in Wily 15.10 at release in October if not already using it). 

Good luck.

---

### Post by v3.xx on 2015-07-01
> (I believe the 4.1 kernel will be included in Wily 15.10 at release in October if not already using it). 
4.x hasn't made it to wily yet.  Shouldn't be too far off I would think.

---

### Post by tgalati4 on 2015-07-01
Well, to evaluate a new kernel, you typically download the source code, set up your build environment (install *build-essentials* and other packages) compile the kernel, and run it.  Check the log files for errors and then run test suites (like *phoronix-test-suite*) to run tests and collect statistics between the old kernel and the new kernel.  Differences in performance are noted and reported.

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

So I would say the first step is to try to compile the latest kernel and take note of the steps that you tried and the errors you encountered.

---

### Post by zika on 2015-07-01
@lyf: Or You could use [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D) for fast(er) approach. I do that even though I've compiled kernels on my own following great advice(s) from [MilosSD]("http://forum.ubuntu-rs.org/Thread-kompajliranje-linux-kernela-na-ubuntu") and [Punky]("http://forum.ubuntu-rs.org/Thread-old-school-kompajliranje-kernela-za-svaki-distro")... Not enough hours in a day to compile and to follow daily development of kernels... ;)

---

### Post by lyf on 2015-07-03
Hi Tgalati,

I had downloaded the latest kernel and compiled with the default configuration by issuing the command "make all" and it generated the image bzImage in arch/x86/boot/bzImage.

Also I had downloaded the photonix-test-suite.

Now how to test the same and whether above mentioned steps are right ?

Regards,
Lyf

---

### Post by tgalati4 on 2015-07-03
You should be able to install the kernel along side your current kernel with:

```
sudo make install
```

Then run GRUB2 update to detect the multiple kernels and make menu entries that you can choose from.

```
sudo update-grub
```

Boot into the new kernel, look for problems in *dmesg*.  Take notes.

```
dmesg | more
```

Run some phoronix tests and upload the results to their website.  Run the same benchmarks on your current/existing kernel so you can compare.  

Understand that new kernels may have debugging symbols, checkpoints, and other profiling instruments installed during the development cycle, so they may run slower.

Spend some time with *strace* if you are interested in profiling parts of the kernel, versus overall system performance.

```
man strace
```

---

### Post by lyf on 2015-07-06
Hi Tgalati,

Thanks for the resply.

Is there any meachanism to roll back to the previous kernel version if something goes wrong ?

Regards,
Lyf

---

### Post by dino99 on 2015-07-06
> **lyf said:**
> Hi Tgalati,

Thanks for the resply.

Is there any meachanism to roll back to the previous kernel version if something goes wrong ?

Regards,
Lyf

you can get more than one kernel installed at once; so you still can select an other one to boot with

---

### Post by tgalati4 on 2015-07-06
HIt Escape during boot, so the GRUB2 menu shows up.  Use the arrow keys to select any previous kernel that you have installed on your system.

---


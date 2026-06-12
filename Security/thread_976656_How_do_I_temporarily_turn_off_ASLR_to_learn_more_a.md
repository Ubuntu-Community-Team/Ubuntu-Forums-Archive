---
title: "How do I temporarily turn off ASLR to learn more about buffer overflow?"
date: 2008-11-09
forum: Security
---

### Post by kittkatt on 2008-11-09
Hello everyone,

I am currently going through [a security primer book]("http://www.amazon.com/Gray-Hacking-Second-Shon-Harris/dp/0071495681/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1226260079&sr=8-1") out of self interest.  Right now I'm at the buffer overflow section of the book and discovered that I can't try out the examples in the book because of the [recent implementation of ALSR into the OS.  ]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security")

I am just wondering if anyone knew how to temporarily disable this feature (while I try out the sample programs) and then enable it back when I'm all finished.

I am running Ubuntu Hardy 8.04.

Thanks in advance :)

---

### Post by cariboo on 2008-11-09
The kernel hardening is done right in the kernel itself so it is pretty tough to turn it off. You might have to find a distribution that is running a 2.4 kernel to test the examples.

Jim

---

### Post by randy78 on 2008-11-09
You also may want to set up a virtual disk inside VirtualBox, so you don't accidentally kill your system ;)

I find it's the best way to learn, because if something goes wrong, you can start over from scratch :guitar:

---

### Post by Gamma746 on 2008-11-10
You'd need to recompile your kernel and all your programs.  Just run something in VirtualBox; it'll save you some trouble.

---

### Post by aashay on 2008-11-15
Or maybe you could try using the -fno-stack-protector parameter while compiling the code with gcc

---

### Post by teddks on 2008-11-16
Lack of a stack protector won't help the ASLR.

What I do is just run old Red Hat installations on VM's. Grab something nice and old like Red Hat 6 or something, fresh out of the 90's.

---

### Post by beenudel1986 on 2009-05-01
It can be disabled by

echo 0 > /proc/sys/kernel/randomize_va_space

u need to be root (su root)

---

### Post by shanwu on 2011-06-02
> **beenudel1986 said:**
> It can be disabled by

echo 0 > /proc/sys/kernel/randomize_va_space

u need to be root (su root)
beenudel1986,
            How do you know if ASLR is truly disabled after you input the command:
echo 0 > /proc/sys/kernel/randomize_va_space

---

### Post by AmbientShade on 2011-06-28
> **shanwu said:**
> beenudel1986,
            How do you know if ASLR is truly disabled after you input the command:
echo 0 > /proc/sys/kernel/randomize_va_space

This is not the most trivial method to ensure that ASLR is turned off, but this method works.

There is a "maps" file in /proc/PID where PID is the process ID of a currently executing process.  (You can run a program and `ps -e | grep PROCESS_NAME` or `pgrep PROCESS_NAME`; the PID will be listed.)  The "maps" file shows the virtual layout of the process by showing the hexadecimal addresses of the virtual address ranges.

If you turn ASLR off, the addresses will be assigned deterministically.  With ASLR turned on, the addresses will be assigned randomly.  The "maps" file will reflect the changes as expected.

Please keep in mind that /proc/PID/maps will only exist for as long as the process exists.  As soon as the process finishes execution, the entire PID directory will be removed from procfs.  You may need to create an infinite loop somewhere in the process to view the "maps" file at that time.

Furthermore, you will only be able to view the /proc/PID directory contents if you have privileges to view that directory.  You may need to sudo su or sudo vi to view some of the OS process directories.

I hope that this helps.
-AS

---

### Post by bodhi.zazen on 2011-06-28
Cut to the case and download DVL .

---


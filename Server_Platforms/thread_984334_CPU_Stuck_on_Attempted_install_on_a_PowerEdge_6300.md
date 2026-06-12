---
title: "CPU Stuck on Attempted install on a PowerEdge 6300, possible fix, need help applying"
date: 2008-11-16
forum: Server Platforms
---

### Post by LordV on 2008-11-16
Hello everyone,

I recently acquired an old Dell PowerEdge 6300 to replace my old ubuntu server. So when trying the install 8.04 Server (x86), right away it comes up and says, 

"BUG: soft lockup - CPU#2 stuck for 11s!"

Now, i seem to have maybe found a solution at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214814)

where the poster there released a patch for Hardy specifically for the 6300. The issue i'm having (being a linux newbie) is that i have no idea how to apply this patch to an install disk!


Any help is GREATLY appreciated,
Thanks

---

### Post by cariboo on 2008-11-16
You could compile a new kernel using this howto:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Or you could check with Dell to see if they have a patched kernel for your particular computer.

Jim

---

### Post by LordV on 2008-11-16
Reading this

[http://linux.dell.com/distributions.shtml](http://linux.dell.com/distributions.shtml)

suggests that ubuntu server isn't currently a viable option. The way you suggested (being a linux newbie) is probably not the easiest option, and i'm hoping to do this without having to dig to my old server to compile the kernal. If there is any possible way, please let me know, I don't want to have to migrate to Red Hat, or SuSE, or in the end going to a windows server.

---

### Post by LordV on 2008-11-17
SOLVED: It seems that ACPI was stopping it, so putting acpi=off in the boot sequence fixed it.

---


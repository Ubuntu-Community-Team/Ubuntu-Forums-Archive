---
title: "Building Kernel on SPARC"
date: 2006-08-25
forum: Sun Sparc Users
---

### Post by clarsen on 2006-08-25
I've been able to install Ubuntu 6.06 on a SPARC machine.  I also have (I think) all of the source code files loaded.  The problem is that there doesn't seem to be gcc or other software development tools.

- How do I bootstrap the developers environment?
- Or, where can I download suitable binaries?

Thanks,

Chris

---

### Post by fajensen on 2006-08-26
What's wrong with:  sudo apt-get install gcc  ??
                    sudo apt-get install kernel-source ???

Might need to edit /etc/apt/sources.list to gain access to stuff that can break your system.

Be aware that this will give you the ubuntu-patched sources for kernel 2.6.15-25. 

SPARC support was stopped for a long time in kernel 2.6.16 and is now back in 2.6.17 and up (I think Gentoo actually have 2.6.16 kernels for SPARC). You might as well go for the latest "stable" kernel from [http://www.kernel.org/](http://www.kernel.org/).

I would build the ubuntu-patched version first to verify that the tools work (and figure out how they work).    


PS:

If installing gcc hard, then I think that you will have real trouble building a kernel that actually work. The SPARC build appears to be *very* sensitive to the kernel konfiguration and the defaults do not work (on my box anyway). The easiest is to Google for a kernel config that works for your architecture!

---

### Post by clarsen on 2006-08-30
> **fajensen said:**
> What's wrong with:  sudo apt-get install gcc  ??
                    sudo apt-get install kernel-source ??? AFAIK nothing is wrong with this procedure.  The problem is that I didn't know what the procedure was on Ubuntu.  If fact, I did what you suggested and it works just fine!  Thanks.
> PS:

If installing gcc hard, then I think that you will have real trouble building a kernel that actually work. The SPARC build appears to be *very* sensitive to the kernel konfiguration and the defaults do not work (on my box anyway). The easiest is to Google for a kernel config that works for your architecture!  What do you mean by "installing gcc hard"?

I've build Linux kernels for Intel/AMD systems but never before for SPARC.  But even my Intel/AMD experience is limited; I'm really a Solaris guy.

Thanks,

Chris

---

### Post by Delta_Farce on 2006-09-01
You might have some luck checking the Gentoo Sparc Handbook. I built 2.4 and 2.6 kernel in Gentoo with almost no problems (except once when I left out the right network driver). The handbook will tell you exactly what you need for Sparc systems and it should be translatable into Ubuntu.

---

### Post by clarsen on 2006-09-01
> **Delta_Farce said:**
> You might have some luck checking the Gentoo Sparc Handbook. I built 2.4 and 2.6 kernel in Gentoo with almost no problems (except once when I left out the right network driver). The handbook will tell you exactly what you need for Sparc systems and it should be translatable into Ubuntu.

Thanks!

Chris

---

### Post by tedgent on 2007-03-09
Were you able to successfully build using the Gentoo pages? I need to build a t2000 kernel for debug purposes to fully investigate a gettimeofday() issue.

thanks ted

---

### Post by tedgent on 2007-03-12
Answered my own question, I followed the instructions on Building a Kernel the Ubuntu Way on my T2000 system. The kernel I built was 2.6.17.14. The build was successful. The dpkg install correctly placed the bootable images in /boot and linked the original as a backup. The T2000 uses SILO as the boot loader.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

This procedure is also documents in the Ubuntu Hacks book from O'Reilly

If you would like further information please reply.

thanks ted

---


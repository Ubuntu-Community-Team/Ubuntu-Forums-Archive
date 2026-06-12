---
title: "32Bit RT-Kernel with PAE??"
date: 2009-09-25
forum: Server Platforms
---

### Post by Sorehead on 2009-09-25
Hello!

I'm trying to install Ubuntu Server on an IBM XSeries365 with 4 Intel XEON CPUs and 12GB RAM.
These CPUs does not support 64-Bit OS, so i have to use the 32Bit Version.

When I installed 8.04LTS and 9.04 with the standardkernel I got PAE activated and got access on the whole 12GB of RAM.

But after installing the actual RT-Kernel (which I need) I could only use 4GB of RAM.
Does the RT-Kernel not habe the PAE feature?

I hope you can help me solving this problem..

Regards, Sascha

---

### Post by scorp123 on 2009-09-25
What do you need the RT kernel for?? RT only makes sense when doing audio processing on a professional level. For servers it's not going to do anything. Many newbies think "real time kernel == faster machine" ... that's BS, sorry to say so.

Then ... I find it bizarre that IBM would build a system that can accept up to 32 GB RAM with 32-bit CPU's?

Taken from this IBM manual here:
[http://www.redbooks.ibm.com/redpapers/pdfs/redp3826.pdf](http://www.redbooks.ibm.com/redpapers/pdfs/redp3826.pdf)

" ... With 16 sockets and using 2 GB DIMMs, the x365 can have up to 32 GB RAM."

Are you really really sure you can't run 64-bit? What's the output of this command:

```
cat /proc/cpuinfo
```

---

### Post by lykwydchykyn on 2009-09-25
Ah, the lost art of compiling your own kernel...  I think that's the only option, if you want PAE + RT.  Have a look here:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Like scorp123, I wonder why you need RT?

---

### Post by scorp123 on 2009-09-25
> **lykwydchykyn said:**
> Ah, the lost art of compiling your own kernel...   :lolflag:

---


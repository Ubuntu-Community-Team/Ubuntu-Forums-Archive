---
title: "So... I want to really get into the kernel"
date: 2010-05-26
forum: The Cafe
---

### Post by clgy15 on 2010-05-26
Hey guys,
Love linux been on it for years. But I really want to be able to really know whats going on in the kernel so I thought I would just throw myself into a very very basic distro to try it on. I tried LFS but its slightly confusing for me.... What is something else I can try to really grip how to work the kernel. I pretty much want to learn from the ground up how linux runs so I can really get into it because Linux will always be my OS so I want to really know it.
Thanks

---

### Post by TheStroj on 2010-05-26
You can visit kernel.org and download the source code and see it for yourself :D. The package is not that big so it shouldn't be a problem :)

Note: viewing the files will be much easier if you extract them first :P (trust me, not extracting them is a pain in the ***)

---

### Post by clgy15 on 2010-05-26
See I want to do that, I know C++ like nothing. I understand the code but I dont understand the logic, the setup or the purpose. Thats really what I need

---

### Post by undecim on 2010-05-26
You can install VirtualBox and mess around with distros.

If you want to get really deep (like TheStroj mentioned about reading the source codde) you should learn how to write C.

Another good thing to check out might be the boot process. Learn how grubs loads the kernel, how the files in the initrd work, what they do, etc.

---

### Post by clgy15 on 2010-05-26
Is there like a commentary or something that says what each file in the kernel does and what links to it and all that? That would make my day so much.

I know C and C++ very well, its not my lack of understanding, its just a lack of understanding why and what does what

---

### Post by TheStroj on 2010-05-26
> **clgy15 said:**
> See I want to do that, I know C++ like nothing. I understand the code but I dont understand the logic, the setup or the purpose. Thats really what I need

This can explain a lot:
[http://duartes.org/gustavo/blog/post/kernel-boot-process](http://duartes.org/gustavo/blog/post/kernel-boot-process)

I don't understand a lot, but it's still cool to read it.

---

### Post by clgy15 on 2010-05-26
See that explains alot of the boot process and now I know how the kernel loads. It now has me curious how the code completes these tasks.... Hmmm I wish there was a commentary on the actual code

---

### Post by mickie.kext on 2010-05-26
If you want to start with hacking kernel, and you already know C, this site is for you:

[http://kernelnewbies.org/](http://kernelnewbies.org/)

---

### Post by TheStroj on 2010-05-26
First part of the text explains a bit of how the kernel actualy works: [http://www.linfo.org/kernel.html](http://www.linfo.org/kernel.html)

First thing i read about Linux kernel was this (good old wikipedia): [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

For more info, there are MANY links in the text on the wiki page so you can find most of the info you want.

If you will still need help finding articles about kernel, i will help you out tomorrow :).

---

### Post by clgy15 on 2010-05-26
Haha wikipedia its so great. Its starting to come together. Though im worried about the 5.3 million lines of code :(. 

Okay so I understand what the kernel does... generally.
Iv got the 2.6.34 source code and I really wish there was a "This is the first page that contains the simple functions" .......... Where should I start in the source?

---

### Post by Phrea on 2010-05-26
> **clgy15 said:**
> Haha wikipedia its so great. Its starting to come together. Though im worried about the 5.3 million lines of code :(.

From Wikipedia: 
16 May 2010 - Linux 2.6.34 was released (13,320,934 lines of code).

---

### Post by BoneKracker on 2010-05-26
> **TheStroj said:**
> First part of the text explains a bit of how the kernel actualy works: [http://www.linfo.org/kernel.html](http://www.linfo.org/kernel.html)

First thing i read about Linux kernel was this (good old wikipedia): [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

For more info, there are MANY links in the text on the wiki page so you can find most of the info you want.

If you will still need help finding articles about kernel, i will help you out tomorrow :).

A good next step beyond that is to begin manually configuring and compiling your own kernel.  You can do that in virtually any distro.

---

### Post by Ibidem on 2010-05-26
Try the [Linux Kernel Hackers' Guide]("http://tldp.org/LDP/khg/HyperNews/get/khg.html").  It probably will be good for starting, though perhaps not everything is up-to-date.
Are you interested in how the kernel itself works, or how drivers should be written?

---

### Post by clgy15 on 2010-05-26
Most definetly how the kernel runs. Im really curious

---

### Post by clgy15 on 2010-05-26
> **Ibidem said:**
> Try the [Linux Kernel Hackers' Guide]("http://tldp.org/LDP/khg/HyperNews/get/khg.html").  It probably will be good for starting, though perhaps not everything is up-to-date.
Are you interested in how the kernel itself works, or how drivers should be written?

Nice guide! It even says what files do what! That helps!

---


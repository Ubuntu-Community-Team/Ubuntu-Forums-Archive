---
title: "Compiling a small as possible linux kernel"
date: 2012-10-03
forum: The Cafe
---

### Post by Kaninsopp on 2012-10-03
Hi guys,

i wanna ask you for help to compile a very tiny kernel. I'm currently having a task at school that dictates that I must compile a kernel without modules, that can boot and is less than 10mb big. I've tried a load of stuff but I tend to kill modules I need and forget to bake the important options in to the kernel. 

I don't need anything really but keyboard and a functioning terminal when I boot. Can someone clever please point me in the right direction? :-)

Thanks!

---

### Post by Majlo on 2012-10-03
Hello,

I have always used kernel configs ( vanilla ) from webpage [http://kernel-seeds.org]("http://kernel-seeds.org") .They are pretty tiny and always work for me .Please see howto first.Basically you just need to add your hardware and you are done.

---

### Post by oldos2er on 2012-10-03
Not an Ubuntu support question; moved to Community Cafe.

---

### Post by anaconda on 2012-10-03
How about taking a 2.4 kernel.
I know. a bit old, but also very small.
For example DamnSmallLinux (DSL) used it. 
kernel versions 2.6 and later are a lot bigger

---

### Post by mips on 2012-10-03
Maybe have a look at Tiny Core Linux as it's only 8MB in size.
[http://distro.ibiblio.org/tinycorelinux/downloads.html](http://distro.ibiblio.org/tinycorelinux/downloads.html)

---

### Post by ssam on 2012-10-04
there is a
```
make modconfig
```
that enables the module for every module reported by lsmod. so in theory if you boot a standard dristro kernel. plug in everything you need, and run that, the .config file will have everything you need enabled. you could then run
```
make menuconfig
```
and change the Ms to Ys to get them built in.

beware though. I was unable to get a radeon card working with it built in to the kernel. it needed to be a module, so that it could load the microcode/firmware for the card. (the other work around in this case was to disable radeon KMS).

---

### Post by Kaninsopp on 2012-10-06
Hm, thanks for suggestions guys. Still having trouble making it work for some reason. Don't understand why tho, but I somehow manage to try and kill my init. That sucks, so kernel panick is my friend right now.

---

### Post by XBMC old School on 2012-10-06
It sounds like this might be below your user level but I found this [3 part tutorial ]("http://www.youtube.com/watch?v=XAo1QCQXODo")helpful in recompiling my Kernel (skipped the BFS & BFQ).

---


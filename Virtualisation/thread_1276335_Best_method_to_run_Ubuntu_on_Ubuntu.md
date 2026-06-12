---
title: "Best method to run Ubuntu on Ubuntu?"
date: 2009-09-26
forum: Virtualisation
---

### Post by bakegoodz on 2009-09-26
What is the best performance way to run a instance of 32 bit Ubuntu on 64 bit Ubuntu? Before anyone start screaming "Why in the world you would do that?" Trust me I've explored my options, explaining my need will just distract from the question. I want a solution that doesn't need the hard drive visualized, it can just run in a folder. Can KVM do this? Is there something like chroot, but more elegant? I found howto almost five years old, that details how to a do this with a chroot, but it seems pretty kludgey. [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

### Post by gordintoronto on 2009-09-26
Virtualbox!

---

### Post by falconindy on 2009-09-27
chroot is definitely the way to go. I do this to save myself some headaches when assembling NASM programs. The guide you reference is actually the same guide I found and followed. Worked great for me. Typical operation is something like:
```
dchroot -d
nasm -felf file.asm
ld file.o -o file
^D
./file
```Where are you running into problems?

---

### Post by bakegoodz on 2009-09-28
Still researching, I think UML or Vserver, might be what I want. Any insight?

---

### Post by dpj23 on 2009-09-30
VMware hands down...

---

### Post by scrooge_74 on 2009-10-01
Virtualbox also good

---

### Post by juancarlospaco on 2009-10-02
KVM, because the kernel is optimized for KVM, 
because its the main virtualization technology choosed by Ubuntu.

---

### Post by bakegoodz on 2009-10-27
I found chroot to be best, though there are some weird bugs I don't understand how to work around yet.

---


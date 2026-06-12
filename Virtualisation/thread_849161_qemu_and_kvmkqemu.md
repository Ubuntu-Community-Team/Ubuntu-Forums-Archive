---
title: "qemu and kvm/kqemu"
date: 2008-07-04
forum: Virtualisation
---

### Post by andrew_awp on 2008-07-04
i was wondering, and cant find anything in the man pages, about how qemu decides to use kqemu or kvm as the backend if both are installed. not that it matters much, i guess the benchmarks are about equal.

i also have xen installed, but virtual machine manager craps out when trying to connect. but i would rather use para-virtualization, and seems cannot with kvm or qemu.

---

### Post by igwk on 2008-07-05
kvm includes qemu, so you wouldn't run qemu directly.  You'd just run kvm and it would use QEMU for some of its virtualization work.

---

### Post by andrew_awp on 2008-07-15
oh. well, somewhere i read about benchmark comparisons between the two, so maybe they are talking about a kde interface?
i have decided to go with virtualbox for now, a whole lot easier to deal with. cant seem to get xen to go at all, the vm's always start in a 'no state'. also can use the vm's in windows, linux or solaris, so doesnt matter what os i boot into, as long as i use a readable partition for that os. i suppose vmware could do the same. actually, seems virtualbox is basically a ripped vmware...

---


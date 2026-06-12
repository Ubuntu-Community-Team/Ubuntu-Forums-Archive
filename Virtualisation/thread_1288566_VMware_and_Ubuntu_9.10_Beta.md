---
title: "VMware and Ubuntu 9.10 Beta"
date: 2009-10-11
forum: Virtualisation
---

### Post by fjgaude on 2009-10-11
Say, has anyone figured out how to install VMware Server 1.09 with Karmic Beta? Thanks!

---

### Post by bartcramer on 2009-10-11
Erm, no. I use Fusion, which works, until I install vmware tools. It says that it can't find X.org, makes a new one, and when it restarts, it gives a black screen. No terminals, nothing. Tried with Alpha 6 and Beta. Also, because the kernel is not recognized, new modules have to be compiled. However, not all is fine, and things do not compile well (loads of warnings, and some modules don't compile), and the VM is unusable after restart (just a black screen). 

Any help/hints are appreciated!

---

### Post by fjgaude on 2009-10-11
I'm no programmer... so we'll have to wait until someone who is finds a solution... else... we go to KVM, eh?

---

### Post by darco on 2009-10-23
This may help you.....

[http://ubuntuforums.org/showthread.php?t=1297939](http://ubuntuforums.org/showthread.php?t=1297939)

good luck

darco

---

### Post by fjgaude on 2009-10-24
Thanks, darco! I think I'll wait for the final release of 9.10 hoping that someone will have an easy patch without full kernel re-compile. I would like to continue to use VMware Server 1.09 and not go to 2.xx... or I may just switch over to KVM if an easy way doesn't show for 1.09.

Thanks again!

---


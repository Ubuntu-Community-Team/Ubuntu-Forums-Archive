---
title: "VirtualBox freezing the entire system"
date: 2012-04-13
forum: Virtualisation
---

### Post by fddvbv on 2012-04-13
I'm trying to run Snow Leopard using virtualbox, and every time I run OSX, my entire system freezes at the "boot:" option. I can't even type '-v' or anything before it freezes. I believe it's virtualbox 4.0.4, and Ubuntu 11.10 (or the most recent one...I just upgraded.) I've never set up a VM before (I've only used a VM once or twice, and it was running linux in Windows). I've tried limiting it to 512mb base memory, and I've tried giving it 2gb, but neither works. I have virtualization enabled in BIOS. None of the fixes i've found solve the problem. 

Any help or ideas is much appreciated!

---

### Post by fddvbv on 2012-04-13
I seem to have solved it. 

I disabled VT-x/AMD-V, and it seems to be working...Or at least it's not freezing Ubuntu anymore.

---


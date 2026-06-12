---
title: "Installing 64 bit jaunty , Virtual box on XP"
date: 2009-04-11
forum: Virtualisation
---

### Post by zenithdave on 2009-04-11
Dumb question alert !

Ive had to install XP again as i need my music apps :D so not to lose touch with ubuntu i have installed the 64 bit on Virtual box running on a 32 bit XP so the question is, is jaunty 64 bit using 64 bits ?

Cant be arsed with all this dual booting when i make Jaunty full screen there is no difference and its quite cute to have it running in a small window, means i can keep testing the Studio :P

Thanks

---

### Post by bodhi.zazen on 2009-04-11
I assume so as I found out earlier, if you are not emulating a 64 bit CPU in virtualbox, 64 bit Ubuntu will not boot.

Open a terminal in Ubuntu and enter :

```
uname -a
```

---

### Post by zenithdave on 2009-04-12
```
********-vb@********-vb-desktop:~$ uname -a
Linux ********-vb-desktop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64 GNU/Linux

```

There we go. Certainly looks like it. It's quite a strange one as XP boots faster than ever in VB if 64bit jaunty is the host but the other way around is a lot slower.

Interesting.

---


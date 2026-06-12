---
title: "[BUG in gthumb]  Testing needed"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by medvedko on 2012-04-11
Hello, dear madams and sirs!

I've probably discovered a bug in gthumb. On some pictures program sigfaults. Did not find any workaround for this. Except for editing+resaving photo. 

The same bug happen on both my PCs. Both were Ubuntu 11.10, recently upgraded to 12.04. Platform is x64, CPU Core2Duo. 4GB RAM. Desktop environment - xorg+Windowmaker. Otherwise both PCs are rock stable. Before upgrade to Precise, files opened fine.

I have many such photos. Here is an example (5MB).

[http://medvedko.dyndns.info/1.jpg](http://medvedko.dyndns.info/1.jpg)

p.s. I'm not megahacker and cannot fix problem by myself. Used gdb on core file and it said:

Program terminated with signal 11, Segmentation fault.
#0  0x00007fec6b14a810 in g_markup_escape_text () from /lib/x86_64-linux-gnu/libglib-2.0.so.0

---

### Post by medvedko on 2012-04-11
Do you have the same problem on this pic?

If the bug will slip into RELEASE, that would be terrible. :confused:

---

### Post by dino99 on 2012-04-11
report that issue & describe how you get it:

ubuntu-bug libglib2.0-0

you'll be asked to open a launchpad account

---

### Post by ubuntu27 on 2012-04-11
Hi medvedko. Create a new user account on your computer, and try what you were trying to do again. 


If you are successful in pulling what you were trying to do with the new user, then, it is most likely not a bug, but a bad configuration (corrupted) in your user.



If you still encounter the problem press **ALT+F2**
and type 
```
ubuntu-bug libglib2.0-0
```, and press ENTER.


Fill the bug report by being descriptive of what you were doing step by step, and what you were hoping to accomplish.


Good luck! :KS


LINKS:

[How to report bugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by medvedko on 2012-04-12
Hmmm... Why "libglib"? Problem seems to sit in gthumb.

---

### Post by dino99 on 2012-04-12
> **medvedko said:**
> Hmmm... Why "libglib"? Problem seems to sit in gthumb.

Does not really matter, devs will change it if needed.

---

### Post by ubuntu27 on 2012-04-12
> **medvedko said:**
> Hmmm... Why "libglib"? Problem seems to sit in gthumb.

It is simply our guess of which package is affecting your use of the program by reading your post.

> Program terminated with signal 11, Segmentation fault.
#0 0x00007fec6b14a810 in g_markup_escape_text () from /lib/x86_64-linux-gnu/libglib-2.0.so.0 


You can still of course do

```
ubuntu-bug gthumb 
```

---


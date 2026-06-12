---
title: "Dan Rosenberg's hacking on 10.04(LTS)"
date: 2010-12-14
forum: Security
---

### Post by cinghegy on 2010-12-14
guys, after a week this 200 lines c code still working, it seems Ubuntu forget it, what happend?

[http://marc.info/?l=full-disclosure&m=129175358621826&w=2](http://marc.info/?l=full-disclosure&m=129175358621826&w=2)

*solved: I build a new kernel (2.6.32.27)

---

### Post by cinghegy on 2010-12-14
Or how to disable econet protocol? I don't need it, thanks for your help.
PS: I'm not a expert level user.

---

### Post by cipherboy_loc on 2010-12-14
It seems to cause a hang on my system. I am using the 2.6.37-2-generic kernel (But on Maverick). It looks like it should give me a shell though...

Imagine if some one injected that into the GNOME/KDE/Fluxbox/etc startup... You log in, and Boom! your system hangs. Which causes you to press and hold the power button... Which repeats over and over again, if the user does not know what is happening...

Cipherboy

---

### Post by cinghegy on 2010-12-14
that's better than on 10.04
it doesn't hang, but gets root

---

### Post by cipherboy_loc on 2010-12-14
Then if you are worried, install the ppa for the Natty kernel version. It is quite stable. It has not crashed once yet (except when I ran that root exploit just now).

If you cannot find the ppa on launchpad, post back.

Cipherboy

---

### Post by cinghegy on 2010-12-15
Thanks, I solved the problem.

---


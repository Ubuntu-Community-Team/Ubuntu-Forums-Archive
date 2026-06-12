---
title: "Turn off TTY (agetty) Power save?!"
date: 2008-08-04
forum: Server Platforms
---

### Post by XeroxGUI on 2008-08-04
Here's the issue:
I (happily) use ubuntu 8.04 Server edition on many servers used for nfs/nis, lighttpd, hypervisors, and an array of applications including some custom apps that my ISP which I administor will be offering exclusively. However, for the servers that need it the most, I attach a monitor/keybord to (as opposed to the many headless configs) in order to run htop (an excellant top alternative) for monitoring load and overall performance. The big issue here, is that after about 10 minutes, the monitors display blank screens, yet are still backlit, from what I strongly suspect is a "power-saveing" feature of agetty, the ubuntu/linux getty alternative. How, pray tell, do I turn this off so I can casually monitor the server loads without having to tap num-lock on the keyboard to wake it up? I would really like to enjoy my games of halo and morrowind at work without actually having to, well, work (work here means getting up and hitting numlock, anything else server-related falls under my definition of fun, save layer 8 issues :lolflag:!)

---

### Post by kerry_s on 2008-08-04
```
xset -dpms
```

man xset

---

### Post by XeroxGUI on 2008-08-04
> **kerry_s said:**
> ```
xset -dpms
```man xset
hmm, get this:
```
xset:  unable to open display ""
```I suspect this is for X, haven't looked at the man page thoroughly though, yet I suspect this is for the X Windowing system (big hint, the "display" option, set by -display), and the servers run no GUI at all, not even X. 

Maybe an energy star disabling command for tty?

EDIT: Yep, the xset command pertains to X explicitly.

---

### Post by kerry_s on 2008-08-04
my bag, try one of these:

setterm -blank 0
or
setterm -powersave off
or
setterm -blank 0 -powersave off

"man setterm" for more info

---

### Post by XeroxGUI on 2008-08-04
> **kerry_s said:**
> my bag (bad?, lol), try one of these:

setterm -blank 0
or
setterm -powersave off
or
setterm -blank 0 -powersave off

"man setterm" for more info
That did it! Thanks a million! 

now, back to my "work"...:lolflag:

---


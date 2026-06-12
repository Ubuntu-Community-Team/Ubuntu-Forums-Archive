---
title: "ubuntu server 10.04 rotate screen"
date: 2010-05-01
forum: Server Platforms
---

### Post by Chal on 2010-05-01
is it possible to rotate the screen in ubuntu server 10.04?

---

### Post by AcidHawk on 2010-06-23
Bump

---

### Post by wojox on 2010-06-23
Explain more in detail.

---

### Post by AcidHawk on 2010-06-24
I have an Ubuntu server that I am using as a NAS server under my desk.

I sometimes do some work on the machine and have a screen attached that is orientated portrait.  This is due to a space limitation.  I also want to run iftop and would like to watch the connections in portrait.

Is there a way to rotate the terminal so it displays portrait?

---

### Post by the-penguin on 2011-02-06
try
```
xrandr -o direction 
```
direction being either left, right, normal, or inverted

regards,
the-penguin

---

### Post by garfonzo on 2011-02-06
Why don't you just open a putty window or a terminal window from your main computer (the one you normally work off of) and watch the data that way? This way you could remove the server's monitor all together, freeing up more space on your desk.

You could have one session just running iftop and another session for doing the actual work. Two birds, one stone, no?
That's what I do.

---

### Post by the-penguin on 2011-02-06
> **garfonzo said:**
> You could have one session just running iftop and another session for doing the actual work. Two birds, one stone, no?
That's what I do.


He has a point...

---

### Post by SeijiSensei on 2011-02-07
> **the-penguin said:**
> ```
xrandr -o direction 
```

By default the server edition doesn't include a GUI so xrandr won't help.

---

### Post by the-penguin on 2011-02-08
> **SeijiSensei said:**
> By default the server edition doesn't include a GUI so xrandr won't help.

ah yes, my bad, I didn't notice that we were discussing server edition.
So we are trying to rotate a tty command line?

---


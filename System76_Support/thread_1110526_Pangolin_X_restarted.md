---
title: "Pangolin: X restarted?"
date: 2009-03-29
forum: System76 Support
---

### Post by gila_monster on 2009-03-29
Okay, I haven't had this happen before. I was checking out a website with Firefox (really the only app I had running besides Pidgin), and wham! X restarted. At least, that's what it looked like. I went ahead and did a restart on the system just to make sure everything was cleared up.

Anyone else experienced this?

---

### Post by Lee_Machine on 2009-03-29
Did you by an chance press Ctrl-Alt-Backspace?

---

### Post by thomasaaron on 2009-03-30
Good thought, Lee Machine. I just read that Ctrl-Alt-Backspace is disabled in Jaunty. You can re-enable it with...

```
dontzap --disable
```

---

### Post by gila_monster on 2009-03-30
> **Lee_Machine said:**
> Did you by an chance press Ctrl-Alt-Backspace?

No, sir. In fact, I was leaning back in my chair with my hands behind my head, believe it or not. That's why it got my attention -- I wasn't doing anything with the box at the time.

Good thought, though.

---

### Post by thomasaaron on 2009-03-31
There's the possibility, though, that you mentally triggered the Ctrl-Alt-Backspace functionality. ;) OK, well there's one theory down the drain.

Here's what to do: The next time it happens, immediately log back into your computer and take note of the time on your system clock (the one in the upper right of your LCD). Then go to System > Administration > System76 Driver > Support > Create. This will create a logs.tar file in your home directory.

Attach that log to this thread and let me know the aforementioned time (which will help me find the location of the questionable X restart).

---

### Post by Lee_Machine on 2009-03-31
Well I have add X.org restart on me before but that was on either unstable releases of x.org I was testing, or with unstable versions of Linux.

The most recent being on Jaunty Beta, from my reading it was common. A fix came down.

---

### Post by gila_monster on 2009-03-31
> **thomasaaron said:**
> Here's what to do: The next time it happens, immediately log back into your computer and take note of the time on your system clock (the one in the upper right of your LCD). Then go to System > Administration > System76 Driver > Support > Create. This will create a logs.tar file in your home directory.

Attach that log to this thread and let me know the aforementioned time (which will help me find the location of the questionable X restart).

Thanks! Will do.

---


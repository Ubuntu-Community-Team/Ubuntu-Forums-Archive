---
title: "Computer wont shutdown sometimes"
date: 2009-07-06
forum: System76 Support
---

### Post by eddietours on 2009-07-06
sometime l would shutdown the computer but it wont turn off it stays pitch black with a dash on the left top part of the monitor 
in order to turn off l need to force the computer any help with this  would be really appreciated :cry:

---

### Post by tessk on 2009-07-06
When it's black, what happens if you press ctrl-alt-del ?
 
I've had the same thing happen (not always, but several times), and when I then press ctrl-alt-del, it gives me the message "failed to shutdown md devices". If you're getting the same thing, I think it's this bug: [https://bugs.launchpad.net/ubuntu/+bug/350207](https://bugs.launchpad.net/ubuntu/+bug/350207)
 
edit: it looks like installing backports may fix this problem. i just installed backports a couple days ago, and haven't had the problem since then, so time will tell ...

---

### Post by tessk on 2009-07-06
if you're on jaunty, here's the command to install backports:
 
```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by eddietours on 2009-07-06
the last error say something like microcode sw error

---

### Post by thomasaaron on 2009-07-07
Did you install backports?

---

### Post by eddietours on 2009-07-07
yes seem ok now running some test

---

### Post by eddietours on 2009-07-08
seems back to normal thanks :guitar:

---

### Post by riseringseeker on 2009-08-14
> **thomasaaron said:**
> Did you install backports?

Tom,

Just so you know, I also installed backports and that seems to have fixed the hung shutdown for me as well.  I didn't want to post sooner as I wanted to make **sure** it did the trick!

---

### Post by thomasaaron on 2009-08-14
That's good news, riseringseeker.

Was thinking about you yesterday while flying back from San Fran on a 757. Take-off and landing from/in Denver scared the bejeebees out of me. Strong cross-winds.

---

### Post by swong on 2009-08-14
Thanks to all.  This is good to know, as it happens to me occasionally.  Although when I press ctrl-alt-del, nothing actually happens.

---


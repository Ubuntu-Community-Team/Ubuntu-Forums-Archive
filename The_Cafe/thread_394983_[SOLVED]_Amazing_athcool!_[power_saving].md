---
title: "[SOLVED] Amazing athcool! [power saving]"
date: 2007-03-27
forum: The Cafe
---

### Post by kko1 on 2007-03-27
Hello!

I've used *athcool* since way back when, to make my machine run cooler and quieter, and save electricity. *Now, I recently borrowed a device (also known as a "thingy" :-)) that actually _measures_ the energy consumption of other devices, and - needless to say - tried it also on the computer.*

I must say _I'm impressed!_ With athcool, my machine runs normal day to day business **_with 47 Watts less_** than without athcool. That's not quite half of the total consumption, but still more than a third. :KS :KS :KS

Needless to say, the machine still can do everything it could before. Of course, if you stress the processor, also the power consumption increases, but at least the power-saving features allow the machine to use less when below the threshold (which seems to be at about 80% processor load).

(The measurement also confirmed that the processor (in my case an Athlon XP 2000+) is the single component that (if stressed) uses most of the power in the box, unless you have one of those silly power-hungry graphics cards. Outside the box though there's an old CRT monitor that uses more... But also the CRT can go from 90W to 57W to 25W to 0,9W in different stages of power saving.)

Still, I'd be happier if power-conscious designs for *desktop computers* - like on laptops - were used more.

kko1

PS. Just wanted to share this - I could've posted also in the Hardware section, but since this isn't "a problem", I decided to stick to the café. ;-)

---

### Post by prvteprts on 2009-06-21
How did you setup athcool? I just installed it via apt-get on an Athlon 64 3000+. Did you do any special configuration?

---

### Post by yabbadabbadont on 2009-06-21
If I remember correctly, you don't really need to do anything to configure it in most cases.  There might have been a config file in /etc/defaults though that you might want to look at.  The main thing is that you need to use update-rc.d so that /etc/init.d/athcool gets started at every boot.  I used to configure it so that it started at level 99 in the S runlevel.

---

### Post by Skripka on 2009-06-21
There are also other CPU governors one can use, that seem more easily configured

---

### Post by gletob on 2009-06-22
```
unless you have one of those silly power-hungry graphics cards
```

Why do you call graphics cards silly?  They're necessary for gaming unless all you want play is Frozen Bubble.

---

### Post by mcduck on 2009-06-22
> **Skripka said:**
> There are also other CPU governors one can use, that seem more easily configured

Athcool is made for older AMD Athlon and Athlon XP CPUs which don't have any other power saving features.

With new processors you can of course get the same benefit with the frequency scaling that Ubuntu supports out-of-the-box.

---

### Post by prvteprts on 2009-06-22
I just found out my chipset doesn't support athcool. It's still cool though (pun intended), as my CPU temperature on idle is around 38C anyway, even though room temperature is 30C.

---


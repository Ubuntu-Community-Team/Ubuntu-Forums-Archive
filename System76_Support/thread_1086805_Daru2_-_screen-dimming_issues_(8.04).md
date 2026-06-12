---
title: "Daru2 - screen-dimming issues (8.04)"
date: 2009-03-04
forum: System76 Support
---

### Post by imhavoc on 2009-03-04
My Daru2 got knocked onto the floor (carpeted, short drop, no big deal) a week ago, and when it hit the floor, it lost power and 'blinked off.' (I've fought with the power issue on this machine from the beginning, but I haven't had problems with it for months.)

When I got the machine running again, I started having problems with the screen dimming that I haven't had any trouble with for months.

Nothing has changed in the /boot/grub/menu.lst, so 
"ro quiet splash acpi=noirq ec_intr=0" is all still in place.

Any time the screen blanks, I have to open the Power Manager, and flick the Brightness setting down and back up to restore the screen to full brightness.

I haven't changed the kernel since 2.6.24-19:
Linux schoolbook 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

I'm stumped.

---

### Post by thomasaaron on 2009-03-04
Do you have any problems if you jiggle the screen back and forth?

You also might want to try to re-seat components (memory, hard drive).

Also, if your *sure* the problem recurred immediately after dropping it, it is probably hardware related.

---

### Post by imhavoc on 2009-03-04
Thomas,

 - It's just dim when it wakes from the screen being powered down while not in use.
 - It comes back when I 'fiddle' with the power manager. 
 - I don't even touch the notebook when I'm at work (external keyboard and wireless mouse).
 - Nothing happens when I move the screen around.

Do you really think it's hardware?

---

### Post by thomasaaron on 2009-03-04
Doesn't sound like hardware, really. But the chances of a software issue occurring after a drop are unlikely.

---

### Post by jdb on 2009-03-04
> **thomasaaron said:**
> Doesn't sound like hardware, really. But the chances of a software issue occurring after a drop are unlikely.

I spent my whole life troubleshooting stuff before I retired and some of my worst problems  were self inflicted when I got off on the wrong track because of improbable circumstances.

jdb

---

### Post by thomasaaron on 2009-03-04
Yep, I've had some problems eat my lunch too because of making the wrong assumptions. Thanks for the reminder, JDB.

So, imhavoc, I understand you to be saying that when the computer is idle, the screen goes blank. Did you check your settings in System > Preferences > Power Management for blanking the screen when idle?

---


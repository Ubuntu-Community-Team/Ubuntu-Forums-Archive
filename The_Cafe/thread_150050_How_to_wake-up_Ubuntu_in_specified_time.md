---
title: "How to wake-up Ubuntu in specified time?"
date: 2006-03-25
forum: The Cafe
---

### Post by cro.smiley on 2006-03-25
I want to create a scheduled task for example to run alarm clock every morning at 8:00.
But i don't wannt to leave my computer on, all the time.

Is it possible to hibernate it and then make it to wake up every morninig at 8:00?
In XP i managed to do that simply by creating Scheduled Task, and enabling wake-up option. So, it is possible.

I tried with apmsleep, but it says:
```
Your kernel does not support APM.

```

Any ideas, what can i try next?

---

### Post by cro.smiley on 2006-03-25
Google i love you!

This is the solution:
sudo echo yyyy-mm-dd hh:mm:ss > /proc/acpi/alarm

The computer wakes-up at given time.
So simple :)

---

### Post by sindhu_sundar on 2009-09-21
Didn't work for me! :/ I have an eee 1000h running eeebuntu. it says i have no /proc/acpi/alarm

---


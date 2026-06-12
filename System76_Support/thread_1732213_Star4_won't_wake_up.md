---
title: "Star4 won't wake up"
date: 2011-04-17
forum: System76 Support
---

### Post by Carleas on 2011-04-17
I have a relatively new star4, and I've recently been experiencing a problem where it won't wake properly from sleep.  It's not all the time, and it's not always under the same conditions, but I've noticed it most often when I've let it fall asleep open.

What's strange is, it seems like it wakes up, but the screen doesn't turn on.  I can hear the fan going, and the blue power light is on, but the screen stays off.  I tried fn-f2 and fn-f7, but neither works.  Sometimes, if I shut it and wait a minute and then open it, it will start as normal.  Other times, it won't (like when it was shut to begin with).  Any thoughts?

---

### Post by ktmhz on 2011-04-18
I have been having this exact same problem. Star4 sleeps, tries to wake up, fan spins and power light turns on but display doesn't come on and no keys work. I have tried everything the above poster has tried. Shutting it and opening it later has not worked ever for me. This problem happens about 1-2 times per week, where I average probably 5 sleep/wake cycles per day.
EDIT: This has happened pretty consistently since I got the machine 2 months ago.

---

### Post by isantop on 2011-04-18
Which version of Ubuntu are you running on your systems?

---

### Post by ktmhz on 2011-04-18
> **isantop said:**
> Which version of Ubuntu are you running on your systems?

10.04, as it shipped with.

---

### Post by Carleas on 2011-04-20
Ditto.

---

### Post by isantop on 2011-04-20
I just want to confirm something. Are you guys using Suspend or Hibernate?

---

### Post by Carleas on 2011-04-20
I'm using suspend, both when I close the lid and when it sleeps through inactivity.

Here are my Power Management settings:
[ATTACH]189579[/ATTACH]

---

### Post by ktmhz on 2011-04-21
I am also suspending the machine, usually with the fn-f4 key. I have mine set to blank screen when I close the lid, but this problem seems to occur more frequently if I sleep the computer with fn-f4, close the lid, and then open the lid to wake the computer. I have been careful to not do that the past few days, and it has not occurred. Could be a complete coincidence, as it has occurred under other circumstances in the past.

---

### Post by isantop on 2011-04-21
Keep testing with that, as it may be that Ubuntu is not receiving the monitor switch wakeup signal.

---

### Post by ktmhz on 2011-07-20
Just as an update to this problem, installing 11.04 seems to have fixed it. The machine hasn't failed to wake up a single time since my 11.04 installation in May, whereas it had previously been failing to wake up on somewhere around weekly on 10.04. Whatever it was, Natty seems to have fixed it.

---


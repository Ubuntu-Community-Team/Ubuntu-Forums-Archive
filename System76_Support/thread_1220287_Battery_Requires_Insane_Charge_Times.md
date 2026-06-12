---
title: "Battery Requires Insane Charge Times"
date: 2009-07-22
forum: System76 Support
---

### Post by jpoRS on 2009-07-22
Panp4i running Jaunty.  Haven't tried anything yet.

I brought my laptop into the living room to do some laptoping, then decided that I wanted to listen to music on the speakers in my bedroom (where my charger is set up).  Maybe a total of 15 minutes unplugged.

I look at the battery charge indicator and see that I am at 95% charge, with an estimated time till fully charged of 5 hours.  WHAT?

Is this for real, or is there a glitch somewhere.

Thanks,
jim

---

### Post by Georgesl on 2009-07-22
Did it actually take that long?  I notice that mine is optimistic for the last few percent of the charge.

---

### Post by jpoRS on 2009-07-22
No.  It charged up in a normal amount of time (I didn't notice exactly how long).

But then a little bit ago, thinking the problem was gone, I unplugged and computed in the living room for awhile.  I came back, plugged it in and it says 5:45 to recharge from 15%.  After charging for about an hour I am down to 4:45 but only about 17% charged.

Thanks,
jim

---

### Post by Scotty Bones on 2009-07-22
I can confirm that. I once saw an 8 hour estimate from %75. But, no, it didn't take any where near that long.

---

### Post by thomasaaron on 2009-07-23
Turn off your computer, remove the battery, remove the ac adapter. Let everything cool down to room temperature. I'd give it an hour just because it's fun.

Then hook it back up. Did that fix the problem?

No? Then shoot me an email and let's try resetting the cmos.

---

### Post by jpoRS on 2009-07-23
It sat overnight and is charged now.  I will run down the battery, and see if it happens again.  If it does I will try what you suggested Thomas.

Thanks everybody!

---

### Post by jpoRS on 2009-07-23
Didn't work.  Will e-mail you tomorrow Thomas.

---

### Post by Dawei87 on 2009-07-28
just wanted to see if you found a fix for this. i have a similar problem

---

### Post by thomasaaron on 2009-07-28
Dawei87, on what computer?

---

### Post by Dawei87 on 2009-07-28
> **thomasaaron said:**
> Dawei87, on what computer?

well, its an hp-dv5. my computer doesnt really read the battery time or level right. i.e. it wont charge all the way to 100% or discharge all the way to 0%, and sometimes it doesnt charge at all, and sometimes when it is charging it will say 17 hours remaining. its a different computer but maybe whatever the fix was could relate to mine as well.

---

### Post by thomasaaron on 2009-07-29
We don't really have a way to test and support hp machines. We specialize in System76 machines.

But you might want to google something like "Jaunty HP-hp-DV5 Power Management Broken" and see if this is a known problem on your system.

Could also be a faulty battery.

---

### Post by Scotty Bones on 2009-07-30
I could be wrong here, but I think this issue is probably related to the [gnome-power-manager doesn't recognize "on battery"]("http://ubuntuforums.org/showthread.php?t=1155641") issue. Just buggy power manager reporting in jaunty

---

### Post by gila_monster on 2009-07-30
GNOME and KDE both have problems with power management -- tried both in the past two weeks, confirmed. I confirmed last night and this morning that things seem to work in Xubuntu, though. Odd.

---


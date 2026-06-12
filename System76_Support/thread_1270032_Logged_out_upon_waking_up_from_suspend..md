---
title: "Logged out upon waking up from suspend."
date: 2009-09-19
forum: System76 Support
---

### Post by jii on 2009-09-19
This started happening a week ago. I close my Gazelle, it suspends. Later I open it, and instead of prompting me for a password and all my apps being open, etc, I'm prompted to login; it's as if I was logged out while the system was sleeping. None of my work is saved of course, which is a huge hassle (I usually have 4-5 desktops in use, virtualbox, etc). It only seems to happen when the system has been sleeping over an hour. If the laptop only sleeps for 15 mins or so, it wakes up normally with everything intact (and in roughly the same number of seconds as windows 7 I might add, which they are touting as a major feature. Go figure).

I'm running pre-installed Jaunty 64-bit on a Gazelle Ultra.

---

### Post by thomasaaron on 2009-09-21
GO to System > Prefs > Power Management. What do you have it set to do when the lid closes? (look under both the ac and battery tab)

---

### Post by jii on 2009-09-21
> **thomasaaron said:**
> GO to System > Prefs > Power Management. What do you have it set to do when the lid closes? (look under both the ac and battery tab)

Hi, both are set to suspend. Here's a full read out:

On A/C Power
[INDENT]Actions
    [INDENT]Put comp to sleep at 30 mins[/INDENT]
    [INDENT]Lid closed: Suspend[/INDENT]
[/INDENT]

[INDENT]Display
[INDENT]    Sleep when inactive 6 mins[/INDENT]
[INDENT]    Brightness 25%[/INDENT]
[INDENT]    Dim display when idle (checked)[/INDENT]
[/INDENT]

On Battery Power
  [INDENT]Actions
[INDENT]    Put comp to sleep at 10 mins[/INDENT]
[INDENT]    Lid closed: Suspend[/INDENT]
[INDENT]    Battery critically low: Hibernate[/INDENT]
[/INDENT]
  [INDENT]Display
[INDENT]    Sleep when inactive 6 mins[/INDENT]
[INDENT]    Reduce backlight brightness (checked)[/INDENT]
[INDENT]    Dim display while idle (checked)[/INDENT]
[/INDENT]
General
  [INDENT]Actions
[INDENT]    Power button pressed Ask me[/INDENT]
[INDENT]    Suspend button pressed Suspend[/INDENT]

[/INDENT]
  [INDENT]Notification
[INDENT]    Only icon when dis/charging[/INDENT]
  [INDENT]Extras
[INDENT]    Use sound in event of error (checked)[/INDENT]
[/INDENT]

---

### Post by thomasaaron on 2009-09-22
Please run your System76 Driver (Install Tab > Install Button) and then reboot. Then try closing the lid and see what happens.

---

### Post by jii on 2009-09-25
I ran the driver, rebooted, then let it suspend for a few hours. Same problem. What a pain.

Can suspend (or waking up from it) fail for some reason? Maybe when it tries to wake up it fails so it just restarts gdm or something. Every time it's logged me out it had been asleep for over an hour, but maybe time isn't really the issue? Maybe something is wrong such that too many suspend cycles in a row, without logging out in between, will eventually make wake up fail or something? I've tried to hibernate in the past and seen the message "not enough swap space" or something like that, maybe something similar is happening with suspend.

---

### Post by gila_monster on 2009-09-25
jii, out of curiosity...are you still using NetworkManager (the default) for your net connection, or did you switch by some chance to wicd?

---

### Post by thomasaaron on 2009-09-25
jii,

That's a good point... and it's testable. Suspend has come a long way in Linux, but the problems we typically see nowadays are related to multiple suspend/resume cycles.

Does the problem ever occur after the first suspend/resume cycle.

---

### Post by jii on 2009-09-25
No gila_monster, I'm still using the stock network manager. Thanks for asking.

My typical usage is to practically never reboot or shutdown the laptop, I just always close the lid to suspend and open it back up later and keep working. It's one thing I love about Linux vs windows, you don't have to always reboot the darn thing. So to answer your question Tom, I'm pretty sure every time it's happened it was not the first suspend/resume cycle since restarting. I'll test it on the first suspend/resume cycle tonight by rebooting and then suspending, then resuming in the morning.

Thanks for the updates.

---

### Post by jii on 2009-10-11
Hey, I moved and went without internet access for a couple weeks. 

Meanwhile, the "logged out upon resuming from suspend" problem is still here, regardless of how many suspend/resume cycles have happened previously that boot. A couple times it hasn't resumed at all, but just shows a black (lit) screen.

At this point maybe we should just wait for the koala to show up in 19 days and see how it's working then. My "always on AC power" power management problem is fixed in Karmic (at least alpha 5), so maybe this resume problem will disappear too.

---

### Post by thomasaaron on 2009-10-12
That's probably a good idea. I know that suspend/resume is working well on all of our laptops, so there's probably something specific to your set-up that's killing it. 

I would do a fresh install of Karmic, though, when it is ready. Otherwise you risk carrying over something that is killing your resume.

---

### Post by jii on 2009-11-01
I did a fresh install of 9.10, and no more resume bug, as expected.

---


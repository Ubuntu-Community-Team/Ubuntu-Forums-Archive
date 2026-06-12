---
title: "basic ignorance: battery level icon has disappeared"
date: 2010-02-07
forum: System76 Support
---

### Post by eljayski on 2010-02-07
from top panel and for the life of me i cannot restore it.  advice much appreciated.  thank you, eljayski

---

### Post by linusr on 2010-02-07
unplug AC power, battery icon should appear..

---

### Post by eljayski on 2010-02-07
thank you for response, but still no battery icon regardless of whether AC adapter is plugged in or not.

---

### Post by ajgreeny on 2010-02-07
I think you will find the icon is in the Notification area applet.  Right click on an empty part of the panel and choose Add to Panel, and add it back, if it is gone.

It may also need some change to the icon settings somewhere in System-> Power-Management.  I have a desktop so am not sure where it is.

---

### Post by linusr on 2010-02-07
> **eljayski said:**
> thank you for response, but still no battery icon regardless of whether AC adapter is plugged in or not.

System -> Preferences -> Power Management -> General -> choose 'Always display an icon'

---

### Post by thomasaaron on 2010-02-08
Did ajgreeny's or linuser's excellent ideas help?

---

### Post by eljayski on 2010-02-08
> **thomasaaron said:**
> Did ajgreeny's or linuser's excellent ideas help?

yes and no.  linuser's suggestion brings the icon up for the session.  upon reboot, though, icon is gone.  suggestions?

also, regarding situation a few days ago when update activity caused a screwup with HAL, is this problem random, or fixed now, or . . . ?

i'm a little reluctant to update, now, and that's probably bad practice.  many thanks, eljayski

---

### Post by thomasaaron on 2010-02-08
As far as I can tell, the HAL breakage was random.

I'm not sure why your notification applet doesn't work in a new session. Does this happen after a fresh reboot, or after a suspend/resume cycle?

Also, are you running from the account you created when you first set up your machine, or from a secondary account.

---

### Post by eljayski on 2010-02-08
i'm running only from original account, afaik

i usually shut off after a session

the no-battery-icon situation *seemed* to happen after the HAL fix--i could be wrong, though, and could be completely unrelated.

always appreciate your help!

---

### Post by eljayski on 2010-02-09
turns out that the battery icon that appears using the power mgt window is the one that displays battery while charging--even when computer is running on battery.  mousing over it does _not_ yield estimate of remaining charge time or %

also, other of my icons are disappearing between bootups, too.  specifically, the shut-down icon.

advice appreciated.  many thanks.  eljayski

---

### Post by thomasaaron on 2010-02-09
Sorry if I'm ignorantly missing it, but...

What System76 model do you have? And what version of Ubuntu are you running?

Kind of sounds like some data corruption is occurring somewhere, since the problem isn't limited to just one icon.

---

### Post by eljayski on 2010-02-09
i have a starling and i'm running 9.10

---

### Post by thomasaaron on 2010-02-10
Wow, I'm not sure.

If applets are disappearing and staying gone, that's one thing. If they're actually coming back... I'm perplexed.

Regarding the battery applet, are you sure your battery applet is securely attached to the computer? Are the little lock tabs in the locked position?

---

### Post by eljayski on 2010-02-10
i will check the battery to ensure that it is snugly attached.  thanks, as always!

---

### Post by gmgj on 2010-02-17
Thanks,  That worked for me!

---

### Post by jdb on 2010-02-17
> **gmgj said:**
> Thanks,  That worked for me!

HA HA !!

I know the feeling, sometimes the simplest little
things are the hardest to discover.

jdb

---

### Post by gmgj on 2010-11-09
After a couple of months of testing my new working assumption is that my battery is in such a state that it cannot report reliable information to the OS.  This is not surprising.  The laptop is over 5 years old, its the original battery and it was pretty much used running on power 99% of the time.  A little searching on Lithium Ion batteries has reinforced this assumption.  So I have taken my battery out, rather than have it constantly recharge.  There was an article on Tom's Hardware on how constant battery recharging consumed more electricity than just running it.

---


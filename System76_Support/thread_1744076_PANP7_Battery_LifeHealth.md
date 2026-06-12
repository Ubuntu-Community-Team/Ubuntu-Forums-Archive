---
title: "PANP7 Battery Life/Health"
date: 2011-04-30
forum: System76 Support
---

### Post by Haymakers9th on 2011-04-30
I've had my PANP7 since about July 2010, most of the time I use it plugged in and rarely ever use it on battery power.

I've noticed though, that it cannot detect charge rate (Ubuntu will never estimate battery life left or time till charged or sometimes won't give me a straight percentage), which honestly hasn't bothered me too much.

But today I ran acpi, and found this:

Battery 0: Full, 100%, rate information unavailable
Battery 0: design capacity 4400 mAh, last full capacity 3857 mAh = 87%


This is a little troubling for a laptop that isn't a year old yet and hasn't spent very much time on battery power.  Has anyone else with the same system checked their acpi -V ?  Or does Sys76 support know anything that might be going on?

---

### Post by ArielSonique on 2011-04-30
Maybe try these solutions: [http://ubuntuforums.org/showthread.php?p=10068139#post10068139](http://ubuntuforums.org/showthread.php?p=10068139#post10068139)

#95 (and Brian's PPA bugfix power package) in that launchpad bug thread helped me calibrate the battery charge in PanP7.

---

### Post by Flyers2391 on 2011-05-01
If you are going to leave it plugged in and aren't planning on using the battery, I would removed the battery from the laptop for a while.  No reason for even a "trickle feature" charge running through it all the time.

---

### Post by isantop on 2011-05-02
As the system is left in use with both AC and battery inserted, it will gradually drain and recharge the battery very slightly, which prevents overcharging. This does gradually degrade the performance of the battery. I would recommend as above; to remove the battery when you aren't using it for long periods of time.

---

### Post by Haymakers9th on 2011-05-04
Thanks, I'll try that for now.

---


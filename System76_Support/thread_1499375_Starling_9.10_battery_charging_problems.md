---
title: "Starling 9.10 battery charging problems"
date: 2010-06-01
forum: System76 Support
---

### Post by mrneglet on 2010-06-01
For the last three days, the battery (Starling 9.10 netbook remix) would only charge very slowly, and only when the computer was on (when off, no charging at all).  

I drained the battery completely, let it cool (it wasn't hot to begin with) then re-plugged in.  It is not charging at all now - it remains on "0.0%".  

Any help would be appreciated!

---

### Post by jml on 2010-06-02
Check out this link.  It may help.

[http://ubuntuforums.org/showthread.php?t=1448153](http://ubuntuforums.org/showthread.php?t=1448153)

Joe

---

### Post by mrneglet on 2010-06-02
Thanks, jml.  I tried that solution already (it appears to be the same problem).  I drained the battery completely; then let it cool for 1 hour; then put it back in.  At first, it would not charge at all.  Today, though, the battery is back to charging extremely slowly - after 5 hours it is at 16%.  If I unplug the charger, the status indicator says "battery is fully charged", but the percentage remains at 16%;  then the status changes to "30 minutes remaining, 15% charged".  It appears to me that something in the system is not reading the battery status correctly, and preventing it from charging.  This happened suddenly, not gradually, and the battery is only 8 months old.  I have been using it according to the "good practices" posted elsewhere.

---

### Post by thomasaaron on 2010-06-02
Please try this...

[http://ubuntuforums.org/showthread.php?t=1454329](http://ubuntuforums.org/showthread.php?t=1454329)

---

### Post by mrneglet on 2010-06-04
Thanks, thomasaaron.  Tried that, it thinks it's fully charged and shuts down from lack of power after a couple minutes.  I had seen your sticky and used it before posting.

Guess it's a warranty thing - battery is only 8 months old and this is a disappointment; I don't think this reflects well on the quality.  

Chinese batteries, that's what you get.  I'll call System76 and start the return process.

---

### Post by smulloni on 2010-06-06
I've also had the same problem with my starling (still 9.04) for the last two days -- since I did a kernel update, in fact.  Given the other reports, it seems pretty unlikely that everyone's battery is failing at the same time.

I might try booting up in an older kernel and seeing what happens.

---

### Post by mrneglet on 2010-07-13
Solution - returned the entire netbook under warranty, returned 10 days later and appears to be fixed.  Although they didn't say what it was, it looks like something internal was preventing it from charging.  It's nothing to do with the battery, contrary to the suggestions above.  To anyone else with the same problem, contact System76 and return it.  Good luck!

---

### Post by Carl Hamlin on 2010-07-15
I've also had this problem with my Starling over the last couple of days, *also* since the last kernel update.

Didn't make the connection between the kernel update and the issue until now. I'll see what happens when I roll it back.

---

### Post by Carl Hamlin on 2010-07-15
My battery was doing the same thing for the last several days. After reading this thread, I rolled back to the previous kernel.

Instant improvement. The battery is charging as fast as it used to now.

I suppose that's good news and bad news. :(

---

### Post by isantop on 2010-07-15
We're not seeing this with the Ubuntu 10.04 LTS kernel. Maybe try updating to Lucid.

---


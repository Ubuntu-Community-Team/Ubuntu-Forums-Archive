---
title: "Bluetooth mouse stops working when virtualbox xp starts"
date: 2011-06-14
forum: Virtualisation
---

### Post by Gibsonbc on 2011-06-14
I am using ubuntu 10.10 and I recently upgraded to Virtualbox 4.0.8 from 3.something.  I installed the new guest additions and extension pack.  I use a bluetooth mouse for my laptop which I enable by pressing Fn+12.  I can use it fine on my host, but when I power up virtual windows xp, the mouse quits working and ubuntu no longer recognizes a bluetooth device on the laptop.  I was able to use my mouse just fine in the previous version of virtualbox.  Has anyone else had this problem or know a fix?  

As a side note, (and possibly connected?) sometimes after I wake my laptop up from suspend, my bluetooth stops working.  I have to reboot and enable it Fn+12 once more and then I'm good to go.  If anyone can fix that, it would keep my headaches away.  Thanks!

---

### Post by Gibsonbc on 2011-06-15
Bump

---

### Post by Gibsonbc on 2011-06-17
bump

---

### Post by Gibsonbc on 2011-06-17
> **Gibsonbc said:**
> I am using ubuntu 10.10 and I recently upgraded to Virtualbox 4.0.8 from 3.something.  I installed the new guest additions and extension pack.  I use a bluetooth mouse for my laptop which I enable by pressing Fn+12.  I can use it fine on my host, but when I power up virtual windows xp, the mouse quits working and ubuntu no longer recognizes a bluetooth device on the laptop.  I was able to use my mouse just fine in the previous version of virtualbox.  Has anyone else had this problem or know a fix?  

As a side note, (and possibly connected?) sometimes after I wake my laptop up from suspend, my bluetooth stops working.  I have to reboot and enable it Fn+12 once more and then I'm good to go.  If anyone can fix that, it would keep my headaches away.  Thanks!


SOLVED:  

So virtualbox was capturing the laptop's bluetooth device when it booted up.  All I had to do to fix the problem was disable this capture from the Devices menu after it starts.  The bluetooth device appears under the USB selection as:  Uknown Device 0A12:0001.  It had a check beside it and I simply unchecked it.  That's it.  My mouse is back.

---


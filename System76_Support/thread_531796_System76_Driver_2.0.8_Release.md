---
title: "System76 Driver 2.0.8 Release"
date: 2007-08-22
forum: System76 Support
---

### Post by crichell on 2007-08-22
Hello All,

Earlier today we released System76 Driver 2.0.8.  This is primarily a release to catch up with our new Santa Rosa systems.  (2.0.7 has been shipping on them for some time.)

This release does include initial Gutsy support, however; the driver won't do much until we've completed our testing and reach Beta stage on Gutsy.

Change Log

Version 2.0.8

   1. Add initial gutsy support
   2. Fix bug in applying piix fix to Santa Rosa laptops 

--------------------------------------

Version 2.0.7

   1. Add new Pangolin Value (panv3) 

--------------------------------------

Version 2.0.6

   1. Add new Darter Ultra (daru2) 


We have a few pending bugs out there that will be fixed in the next driver release.  We'll keep you posted.

Cheers, Carl

---

### Post by sgtron on 2007-08-22
Won't install on my system.  Says file size mismatch.

---

### Post by crichell on 2007-08-22
In update manager click "Check" again to reload your sources file.  Then click "Install".  I made a mistake inserting the wrong file size when I originally uploaded the driver.  That should do the trick though.

---

### Post by sgtron on 2007-08-22
That did the trick.  Go to sleep Carl.  It's after 7pm here.  I know it's like midnight in your country.

---

### Post by palintheus on 2007-08-22
Does this fix the issue on the Daru2 regarding the headphones and mainspeakers?

[https://bugs.launchpad.net/system76/+bug/130669](https://bugs.launchpad.net/system76/+bug/130669)

I installed the driver and when I ran it and clicked on "Install" on the Drivers tab, it said that all hardware is supported by Ubuntu on the Daru2...

---

### Post by thomasaaron on 2007-08-22
I'll see if I can duplicate that on our DarU2.

Yes, the new driver includes the headphone fix.
You might try running the Restore Tab/Button. But if you have made any modifications
to your xorg.conf, it may mess them up.

---

### Post by palintheus on 2007-08-22
I just tried running both the driver and restore, still the same result as the bug, also I have noticed, if I use the FN+F7 to turn the volume down to the lowest setting it does not mute it, although the system tray icon shows it to be muted. Do not know if that could be related.

---

### Post by thomasaaron on 2007-08-22
Hold up.
I may have been wrong. Let me check with Carl to see if that fix came down.

---

### Post by steveneddy on 2007-08-22
There is no listing in the Administration tab for the System76 driver.

Is that important and why is it missing?

---

### Post by palintheus on 2007-08-22
hmm, its important if you have a System76 machine.

If you do and its missing, have you reinstalled Ubuntu?

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

---

### Post by steveneddy on 2007-08-22
> **palintheus said:**
> hmm, its important if you have a System76 machine.

If you do and its missing, have you reinstalled Ubuntu?

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

I haven't reinstalled Ubuntu - I only noticed it after this System76 driver upgrade.

What is the launch command so I can add it back into the Admin menu?

EDIT - I answered my own question when I typed in terminal

```
locate system76
```

and the driver page, or GUI is

```
sudo system76-driver
```

I'll add this to my Admin menu.

Thank you, and please.....come again.

---


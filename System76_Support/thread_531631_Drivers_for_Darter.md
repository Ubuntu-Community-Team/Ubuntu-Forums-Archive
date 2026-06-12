---
title: "Drivers for Darter"
date: 2007-08-21
forum: System76 Support
---

### Post by shingalated on 2007-08-21
The system76 driver showed up in the update manager today, so I installed the update.  i assume this is the drivers for the new darter.  How can I configure the fingerprint reader, I see to GUI for it anywhere.  I assume that was part of this, Tom mentioned it last week...

---

### Post by crichell on 2007-08-22
Hi shingalated.

The finger print reader has not been completed.  The low level driver is complete.  Now it's amatter of wrapping a GTK GUI around it, integrating with PAM, and lots of testing.  I'm working on the project but don't expect anything to show off for about a month (so long as I don't hit to many snags.)

The changelog for the driver is pretty basic stuff:

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

---

### Post by reh4c on 2007-10-07
Carl,
How's the fingerprint reader driver coming along?  It would have been much easier if it had the same reader as the newer Thinkpads.  Then, the Thinkfinger driver could have been used.  I tried it, but no success of course.

Thanks,
Gene

---

### Post by shingalated on 2007-10-07
Same here...twice.  Even if the GUI isn't done any chance you could add the CLI version to the net update?

---


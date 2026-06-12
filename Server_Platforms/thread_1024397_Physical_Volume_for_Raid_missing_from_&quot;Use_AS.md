---
title: "Physical Volume for Raid missing from &quot;Use AS&quot; Menu"
date: 2008-12-29
forum: Server Platforms
---

### Post by dpeters on 2008-12-29
I am setting up a RAID 1 with Intrepid 8.10 and am using the document help.ubuntu.com/810/serverguide/C/advanced-installation.html.
     In the Partition Step, Pg. 1, step 5, Select the "Use As" ... By default this is "Ext3 journaling file system", change that to "Physical volume for RAID". This item is not on the menu.  Anyone know where they hid it?

---

### Post by dpeters on 2009-01-10
Oops, wrong CD.

---

### Post by ptrsdwski on 2011-11-26
Hey, I'm having the same problem. I have one HDD that is Sata and one that is IDE, have em both set up in the computer, but the option is missing. What did you mean wrong cd?

---

### Post by darkod on 2011-11-27
It was better if you just opened a new thread instead of posting in a 3yrs old one. :)

Are you using the alternate install cd to set up RAID? I guess you plan to use software raid and not fakeraid, but in any case the recommendation is to use the alternate cd for desktop system, and of course the server cd for server system.

The standard desktop cd doesn't have raid support although it can be used for setting up fakeraid with few fixes. But don't blame ubuntu if you take this path. :)

---


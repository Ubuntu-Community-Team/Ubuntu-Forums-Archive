---
title: "An undo procedure"
date: 2009-01-10
forum: Server Platforms
---

### Post by dpeters on 2009-01-10
Is there a quick way to undo or restore the system to the state it was in before something went awry. I know it depends .... I am thinking of worse case. Then we might consider less worst cases. 
Scenario 1: Fresh install of OS on a RAID 1 array. It works. Then you start tweaking and the OS breaks because of a bug in a piece of software just loaded, or a config file just edited, etc.
Then you can't boot or you can't shutdown, or you can't do something else. You just want to get the system back to where you were before in the fastest way possible, like "undo".

---

### Post by bluefrog on 2009-01-11
no.

but you could make an image with partimage for example before tweaking.

---

### Post by dpeters on 2009-01-23
Whatever ends up working has to work from a stand alone boot from CD as you apparently cannot back up a live OS. Further, it has to recognize the Ubuntu software raid array. It doesn't seem like Ubuntu Desktop 8.04 or 8.10 recognize the RAID array. This appears to limit the choices.

---


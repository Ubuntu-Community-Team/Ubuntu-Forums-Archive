---
title: "Help with Google Earth"
date: 2008-09-13
forum: West Virginia Team - US
---

### Post by rlduff@suddenlink.net on 2008-09-13
I am attempting to install Google Earth and come up with the following error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can you help me with this problem.  I do have a flash drive logged on which may be the reference to the "E" drive.

---

### Post by tbielawa on 2008-09-22
Are you still experiencing this error?

---

### Post by rlduff@suddenlink.net on 2008-10-05
Yes -

---

### Post by phaed on 2009-04-05
This reply might be a bit late, but I get that error if I have two programs trying to use dpkg at the same time.  dpkg is the package manager, and Synaptic is a graphical front end for it.  So if Synaptic is open, or apt-get is working, you can't install Google Earth until they are done.

---


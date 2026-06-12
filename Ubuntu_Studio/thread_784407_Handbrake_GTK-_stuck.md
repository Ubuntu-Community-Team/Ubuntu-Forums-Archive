---
title: "Handbrake GTK- stuck?"
date: 2008-05-06
forum: Ubuntu Studio
---

### Post by BrokeEnthusiast on 2008-05-06
Okay I have Handbrake GTK installed and to get it running I had to go into the terminal and type mono then where the file is located(I just extracted the tarball on the desktop).  Anyways now I tried for it to read the source file which is a DVD but when it does that the window pops up and says that handbrake is reading the dvd and to be patient.  Well it doesnt actually go away from that screen(ive tried different DVD's) so I was wondering where to start to try to fix the problem.  Thanks for the help!

---

### Post by BrokeEnthusiast on 2008-05-07
bump, any ideas??

---

### Post by BrokeEnthusiast on 2008-05-11
Anyone??

---

### Post by mtgmutton on 2008-06-12
try adding a system monitor to one of your panels. Bear with me... click on it when HandBrakeGTK is in the frozen state, then see if the Handbrake CLI is running. If it is, then just wait for a while (the amount of time depends on your cpu and ram. For me, it is about 1.5-2 hrs with a 3.00 GHz processor and 2 GB of ram). Later, it will stop hogging your memory and you can just end the process. Your file will still be there, most likely complete. The user interface seems to have a major freezing problem, but the actual process doesn't stop with the interface.  Hope it helped  :)

---


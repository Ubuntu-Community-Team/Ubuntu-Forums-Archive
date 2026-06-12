---
title: "terminal and system monitor crashes starling"
date: 2010-03-16
forum: System76 Support
---

### Post by superfrogman94 on 2010-03-16
I have noticed that if i go to the terminal or system monitor the screen will freeze ,turn black and must be restarted (i'm sure this is a kernel panic). I hear this has to do with the wireless card. Anyone have more info on this, and if its possible to fix it?, and do you think this problem will be solved in 10.04? Thank you, by the way i love my new starling (just go it yesterday) and i think system76 has done a great job here. :-)

---

### Post by n0dix on 2010-03-16
Maybe solved the issue, but it's not sure. If the hardware is very new probably yes. Similar happens to me with my Dell Inspiron 6400.

---

### Post by superfrogman94 on 2010-03-16
hmmm.. do you think disabling the driver for the wireless card (temporarly) will stop the crashes? do you think its a good idea to try this?

---

### Post by n0dix on 2010-03-16
One of my friends has similar problems with his wireless card. Maybe disabling the wireless card works at the moment.

---

### Post by thomasaaron on 2010-03-17
This is a known bug. System Monitor, or running iwconfig from a terminal, will cause a kernel panic.

We're not working on it right now because we're trying to get the wireless driver included in Lucid. That probably will fix the issue.

---

### Post by superfrogman94 on 2010-03-17
Thanks For The Help Tom! :)

---


---
title: "Wine with dedicated servers"
date: 2010-12-05
forum: Wine
---

### Post by helpineed on 2010-12-05
Hi, I want to run a dedicated game server using wine on Ubuntu. I would like to know if there would be any performance/network slowdowns if I did this, and if I should use a W****ws server instead?

---

### Post by dankegel on 2010-12-06
Give it a try and file a wine bug if it doesn't work well :-)

You might need to raise the hard ulimit for number of files 
open, depending on the number of clients you have.

---


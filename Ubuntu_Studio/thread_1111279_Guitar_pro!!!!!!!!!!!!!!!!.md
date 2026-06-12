---
title: "Guitar pro!!!!!!!!!!!!!!!!"
date: 2009-03-30
forum: Ubuntu Studio
---

### Post by Urema on 2009-03-30
Hi,

I installed wine and guitar pro perfectly, setting up the midi etc - i was writing just this morning.
However, I got my nvidia driver working there about an hour ago and now guitar pro opens then automatically closes. I dunno if the nvidia thing has anything to do with the diagnosis of this problem but it is the only thing i have changed today.

Any suggestions? Any advice?


N Dean G.

---

### Post by clubsoda on 2009-03-31
You could try running it from a terminal, e.g. wine GuitarPro.exe (or whatever) and see if it spits out any error messages as it dies.  Alternatively, make it crash and then type ```
tail /var/log/messages
``` at a terminal to see if it dropped an error message there.

---


---
title: "Ubuntu One consuming 500 mb ram when idle."
date: 2012-06-04
forum: Ubuntu One (CLOSED)
---

### Post by cdysthe on 2012-06-04
Hi,

I'm a Dropbox convert (I hope!), but after having used Ubuntu One for a couple of weeks I notice a few differences from Dropbox. The most glaring difference is that the sync daemon constantly takes 500MB ram on my system (Ubuntu 12.04 x64). It hogs this amount of memory as soon as I log in, does it's initial sync/check but keeps the memory. All in all it seems to me that Ubuntu One uses more system resources than Dropbox. I am syncing the same folders and files with Ubuntu One as I was with Dropbox. Also, afte I log in Ubuntu One grids at 100% CPU for at least five minutes which can be annoying on a laptop, but is not a showstopper.

I'm wondering if this is a problem on my system, or if Ubuntu One is expected to use that amount of memory even when idle?

---

### Post by mastablasta on 2012-06-07
where did you check the memorry? did you use top command? or htop?
 
no it's not expected to use so much memorry. in fact i have a vbox "mashcine" with it and the whole virtual computer has 512MB ram and ubuntu one doesn't take it all.

---

### Post by cdysthe on 2012-06-07
> **mastablasta said:**
> where did you check the memorry? did you use top command? or htop?
 
no it's not expected to use so much memorry. in fact i have a vbox "mashcine" with it and the whole virtual computer has 512MB ram and ubuntu one doesn't take it all.

I used htop. I removed Ubuntu One and resintalled Dropbox. It used around 80 mb when idle. I'm now back on Ubuntu one and it sits around 480 mb and has for the last 8 hours or so.

---


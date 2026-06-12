---
title: "Desktop sluggish after install"
date: 2010-03-09
forum: Ubuntu Studio
---

### Post by m.lp.ql.m on 2010-03-09
I recently installed UbuntuStudio 9.10 via a regular Ubuntu 9.10 install as outlined here: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)
I did it this way because the UbuntuStudio install disk didn't seem to recognize my wireless card.

So I'm having fun testing out Jack and Ardour and everything else, but my main problem is that the desktop is very sluggish. The Ubuntu menu at the upper left takes a good second to appear after clicking on it. Any sort of dialog box takes 1-2 seconds to appear, and any "OK" or "Quit" button takes a second or two to even register the click and another second or two to actually close the box.

The programs themselves seem to work OK-- recording, saving, playing media all happens at speed, it's just whenever any user interaction is required that I have this problem.

It's a brand new system, so I'm pretty sure it's not the hardware: AMD Phenom II X4 965 64-bit processor with 4G ram. I'm using the 2.6.31-9-rt kernel. 

My Kubuntu partition works fine, and I noticed when I first installed regular Ubuntu that I didn't have this problem either-- it seemed to just start with the UbuntuStudio upgrade.

Any ideas?

---

### Post by trulan on 2010-03-09
Sounds exactly like my Lucid Lynx testing installation. :cry:  I haven't figured out what's going on there though.  So I can't really help, but at least I can sympathize...

I will say that none of my several 9.10 Studio installations act like that.  It's supposed to be snappy, and it's definitely not your hardware.  My machines are much older and run the desktop just fine, except in Lucid like I said.

---

### Post by AutoStatic on 2010-03-09
Check your *~/.xsession-errors* file, that might reveal what is causing the lag.

---


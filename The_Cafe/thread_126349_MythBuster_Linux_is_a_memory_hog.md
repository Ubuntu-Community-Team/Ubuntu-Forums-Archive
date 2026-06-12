---
title: "MythBuster: Linux is a memory hog"
date: 2006-02-06
forum: The Cafe
---

### Post by hillbilly on 2006-02-06
Take a look at the below blog. It give an idea as to why the memory usage seems more when an app is being run.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by majikstreet on 2006-02-06
well I thought linux filled swap first then memory... unlike windows which does memory then swap aka page..

---

### Post by raublekick on 2006-02-06
i read this earlier thi morning, and i smiled.

:)

---

### Post by prizrak on 2006-02-06
[QUOTE=majikstreet]well I thought linux filled swap first then memory... unlike windows which does memory then swap aka page..[/QUOTE]
That is sooooo backwards. Linux doesn't swap to drive unless it runs out of memory, well at least by default you can change that. It doesn't fill up the entire RAM before swapping tho (well in Ubuntu in any case) it gets to a certain percentage before dormant apps get swapped out. Windows on the other hand throws w/e is not being used to the drive and keeps currently active processes in memory only. Makes it a bit slower when accessing swap space (esp since it gets fragmented since it does not reside on its own partition) but leaves more RAM free. This makes it slower overall. Linux is faster cuz you access fast storage (RAM) but it's components and applications also tend to be smaller than those for Windows so RAM useage is not the biggest issue. 
To OP, since when do people think Linux is a memory hog? Overall memory useage of Linux is much less than Windows while running the same things. The only exception I am aware of is Firefox, which for some inexplicable reason takes over a 100MB on Linux. I don't remember what it is on Windows but when I used it I remember it was nowhere near a 100MB even with many tabs open.

---

### Post by aysiu on 2006-02-06
Sounds great in theory, but lately [I haven't been feeling it](http://www.ubuntuforums.org/showthread.php?t=125842).

---


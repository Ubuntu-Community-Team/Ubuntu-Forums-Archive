---
title: "Full Screen Graphics Problems"
date: 2012-02-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by svtguy88 on 2012-02-20
Not sure if this has been reported or not, but I've been on 12.04 daily for about two weeks or so now, and this is starting to get annoying.  For the record, the machine in question is an Intel Xeon with an Nvidia NV37GL (Quadro PCI-e card).

If a window is full screened, only the top ~60% of it gets displayed correctly.  For example, if I have nautilus open, maximize the window and browse to a folder with a lot of files (enough that would typically cover the entire maximized window), I can only see the top half or so of the files.  Everything below ~60% of the way down the screen is not visible (just shows as white space, as if the folder had no more files in it).  However, if I mouse over the area that *should* have files in it, the files are drawn, one by one, as the mouse moves over them.

Also, the same issue is plaguing full-screen video for me.  Any video fill refuses to do full screen - I get the same result as trying to display a folder in nautilus - about 60% of the video is displayed correcly, and the rest is garbled.  I get this result regardless of the player used for the video.

What's strange is full-screen Flash video works fine...

I know it's probably difficult to understand my issue, as it's nearly impossible for me to describe it accurately.  Let me know if I can clear things up any more.

Anyone else having similar issues?

---

### Post by svtguy88 on 2012-04-05
Figured I'd respond to myself.  Beta II is out, and I still have some issues -- wondering if anyone else has the same.

Ubuntu 2D still has the problem I described above.  I did, however, find a workaround.  If I used Xrandr to set my resolution to something other than the default, and then switch it back to the default, everything works fine.

Ubuntu 3D is another story.  I don't have the "full screen" issues I had in 2D, but the icons in the Unity launcher are invisible.  When I hover over an icon, it pops up the title of it, but the entire launcher tray is transparent.

I found some bug reports from 2011 about this, and it seems to revolve around using nouveau...which I am.

---

### Post by svtguy88 on 2012-04-06
I hate to bump my own thread again, but NO ONE else has a transparent Unity launcher???

Guess it might be time for a bug report...

---


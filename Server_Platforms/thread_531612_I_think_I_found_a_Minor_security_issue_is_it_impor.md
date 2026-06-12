---
title: "I think I found a Minor security issue: is it important enough to report?"
date: 2007-08-21
forum: Server Platforms
---

### Post by Paulmd on 2007-08-21
I noticed on several occasions that the repaint function may briefly show leftovers from applications that have already been closed.

Once when I ran lxdoom, the contents of a webpage I had recently visited that session (and closed) appeared on the canvas for a fraction of a second before being overwritten. It has occurred to me that the page was still in RAM, and was marked ad available, but not overwritten.  The secruity issue being that in a multi-user environment, it may be possible to see what other users are browsing.

Also noticed that Ubuntu may briefly display the contents of desktop BEFORE the main password prompt. Again, only an issue in a multi-user enviroment.

The question is: is this important enough to report?

---

### Post by rbprogrammer on 2007-08-21
i have only encountered this problem when logging off or shutting down. but only when i left the applications open when i shut down.  and even then it was only for a second.  in which case i always waited to make sure that i logged off before i left the computer..

but if you have more problems with this, i think you should go ahead and file a report.  but before you do, just make sure it has not been fixed yet..

---

### Post by nowshining on 2007-08-22
I've seen this before, BUT I THOUGHT it was because of Ubuntu Just getting around to supporting the Dells 4600i video card, etc.. so again I have always thought it to be the drivers fault. lolz.. yes I use the internal Video Card....

---


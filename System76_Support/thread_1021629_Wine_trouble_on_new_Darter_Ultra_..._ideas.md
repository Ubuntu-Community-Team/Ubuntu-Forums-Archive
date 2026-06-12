---
title: "Wine trouble on new Darter Ultra ... ideas?"
date: 2008-12-25
forum: System76 Support
---

### Post by Murrquan on 2008-12-25
Hi, all! I bought a new Darter Ultra in the after-Thanksgiving Day sales, and just got to use it today.

Anyway, I tried installing Steam and the POL Viewer (for Final Fantasy XI) on my new machine, but they both crashed. And I know this is technically a Wine problem, but they were working on my old machine (an IBM Thinkpad R51), so I'm trying to figure out in what way this machine is different, so that I can get an idea of where to go. Is it because it is running the 64-bit version of Ubuntu on this thing, maybe?

I will continue to look things up elsewhere, but if anyone has any ideas I would be very appreciative. >.>

**Has anyone else had trouble getting modern Windows games to work in Wine on a new Darter Ultra?**

---

### Post by EnderEcho on 2008-12-25
I'm in the same boat with figuring out installing world of warcraft.

From what I've been toying with it seems to be graphical. Running the intel 4500HD seems to be pretty tricky configuring. A lot of the available help has to do with Nvidia. I'll keep checking in here and hopefully we can get a good thread going for darter gamers.

I got my darter during the thanksgiving sales too.

---

### Post by gameguy43 on 2008-12-26
just wanted to let you guys know that i'm in your same boat.  tried to get CS:source up and running.  i got a consistant GUI crash (xorg restarted) at the loading screen.  interestingly, when i un-checked "allow pixel shader" and turned off vertex shader support in the wine config (and i believe that disabling only one of the two yielded similar results) i was able to actually join a server and play, but text was semi-garbled or just gone, and the framerate was way too low.

i popped in #winehq and someone suggested upgrading mesa3d.  after some brief research, i'm still unclear on what mesa3d is, how to upgrade it, and whether or not this will actually help at all.

so i'm stuck for now, but optimistic that we can at least locate the real issue here, and hopefully solve it.

good luck all, and report back in detail with any progress!

---

### Post by Murrquan on 2008-12-26
That sounds like the most progress any of us have had, gameguy43. I couldn't even get Steam to load. >.> It crashed after like a few seconds, and it didn't even prompt me to install the Gecko libraries. And the POL Viewer isn't a 3d application, I don't think; it's Final Fantasy XI's equivalent of the Steam frontend.

Maybe Google this Mesa3d?

---

### Post by Spr0k3t on 2008-12-28
Trying out HL2/Portal with the DARU3 and the default config (8.10).  I get the same results forcing the directx level or not.  I haven't been able to get CS:Source to work either.  The same issue as mentioned in this thread.  On another computer system with 64bit, I have no problems with either game.

---


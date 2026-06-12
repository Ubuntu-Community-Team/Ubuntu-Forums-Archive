---
title: "Wow on ubuntu 10.10 graphics set to low"
date: 2011-03-09
forum: Wine
---

### Post by Umbrix on 2011-03-09
Hiya,

I have been trying to install wow on Ubuntu 10.10, mainly as it is the only reason I ever swap back to windows.

I am using Wine and have followed the instructions, however I cannot set the graphics above low.

I have a nvidia 330M 1GB card. Ubuntu says it has installed the drivers (automatically though its additional drivers) and I use the nvidia panel to configure my display normally.

Any ideas?

Thanks

---

### Post by Perfect Storm on 2011-03-09
Moved to wine section.

---

### Post by cwwilson721 on 2011-03-09
You cannot set the settings above 'low', because of the way the game is played (using opengl, and wine 'translates' D3D to opengl, so WoW won't let you. WoW thinks you have a less capable card, and sets limits).

But you can set individual settings higher, just not the big slider on the first page.

As I've said many times, I just set things low anyway, except 'particle density' (because it shows the 'sparkle' for objects, and void zones, etc, better). I'd rather have the FPS pwnage using opengl over the eyecandy of D3D anyday.

---

### Post by Umbrix on 2011-03-10
Thanks for the explanation, much better than the usual do this and then that.  :)

---

### Post by cwwilson721 on 2011-03-10
> **Umbrix said:**
> Thanks for the explanation, [COLOR="Red"]much better than the usual do this and then that.[/COLOR]  :)

I agree. While the "do this, do that" approach *works*, having an actual explanation behind it teaches the *why*.

And, since your hardware and Ubuntu setup is different than mine, you almost HAVE to have the 'why'. What will help on my system won't necessarily work on yours, Thus, if you know the 'why', you can figure out the 'what' for your system.

I can't even count the number of times I've gotten a "do this, do that" approach that didn't work, and since I didn't have the 'why', it took forever to get what I wanted working. And a simple 'why' added to the 'do this, do that' would have saved alot of aggravation on my part.

The above applies to ALL things, actually.

Great. A "life lesson" on a Thursday afternoon. I've turned into my Mom.

---


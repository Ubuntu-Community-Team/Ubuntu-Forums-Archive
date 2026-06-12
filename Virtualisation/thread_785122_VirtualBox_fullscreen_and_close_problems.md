---
title: "VirtualBox fullscreen and close problems"
date: 2008-05-07
forum: Virtualisation
---

### Post by lviggiani on 2008-05-07
> Hi all,
I've kubuntu 8.04 with desktop effects (nvidia 169.12 driver) and virtualbox 1.6
I have two kind of problems:

1) Running XP as guest and in full screen mode, if I try to switch back to windowed mode (host+F) the system crashes, black screen, X restarts and I'm back to the kdm login page... :( That was not happening with 1.5.6...

2) If I initiate the shut-down of the guest OS and then I switch to another face of my host desktop cube, when the shut.down is complete and the guest closes, my desktop becomes partially black and the mouse start moving jerky... all I can do then is CTRL+ALT+Back Space... :(

Any idea?

----------------

2008-05-16 UPDATE:
Ok, I played a little bit with that and I have discovered that I can solve problem No. 1 only, with the following workaround:
After kde is started I have to go to System -> Desktop Effects and select "No Effects" then Apply, then "Custom Effects" then Apply again. In this way, Compiz is restarted and the full screen problem doesn't occur any more. BTW, this is definitely not user friendly and problem No. 2 is still there.


Thanks.

---


---
title: "Gunbound"
date: 2009-12-14
forum: Wine
---

### Post by AlphaWhelp on 2009-12-14
I'm trying to get gunbound running which supposedly has a platinum rating, but some of the graphics look messed up, so I checked the wine page and it said it required an installed copy of directx 9, so I downloaded directx and tried to install it, and the install failed, and brought me to a failure window where the only options were back, next, and cancel, and the cancel button was greyed out.  Clicking on next did nothing, so I clicked on back and now all three buttons are greyed out and I can't exit the program at all, right clicking on the window does not give me that option, and I'm using ubuntu netbook remix so I can't xkill the window either.

I guess my questions are...

1. what is the correct wine process to terminate in the system resource manager?
2. how do I get gunbound working optimally?

---

### Post by beastrace91 on 2009-12-14
Are you running Ubuntu on a netbook then I take it? If I recall correctly Gunbound is decently 3D and might have issues running under the poor intel drivers for Linux.

At any rate lets try and help you get it setup properly to start. What Wine version are you running? If you are using 1.0.1, then [upgrade to the latest beta](www.winehq.org/download/deb).

Nextly to install DX9 under Wine check out [Winetricks](wiki.winehq.org/winetricks).

Regards,
~Jeff

---

### Post by AlphaWhelp on 2009-12-14
I am using 1.0.1 but I'm not sure how to upgrade to the beta, in fact, I'm pretty sure I used the instructions on that page to install wine from the very beginning and still ended up with 1.0.1.  sudo apt-get upgrade tells me that it is refusing to download wine upgrades for some reason I don't understand.  Update Manager throws an error box that just says "not all updates can be installed" and then gives a list of possible reasons

---

### Post by quazi on 2009-12-15
I don't expect it to work.  The platinum rating was given to a version of Gunbound that is no longer available.

---


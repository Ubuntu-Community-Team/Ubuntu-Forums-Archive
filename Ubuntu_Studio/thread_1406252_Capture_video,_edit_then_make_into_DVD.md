---
title: "Capture video, edit then make into DVD?"
date: 2010-02-13
forum: Ubuntu Studio
---

### Post by PDA1 on 2010-02-13
I used to use ShowBiz in Windows.

What I want to do is load my video (mini DV) onto my computer, edit the home movie  to provide specific "chapters" (sections of a home movie that aren't relative to each other....like swimming, then another chapter called skiing).  Once the DVD has been made then I can select the Chapter I want to watch using the remote control.

I want to save the file and then burn to DVD so it can play on a typical home DVD player.


Do you have any recommendations for a program that'll do that?

---

### Post by ron999 on 2010-02-13
Hi
I don't know of one Linux program that will do all that.

If you break it down.

Use a program such as **avidemux** to edit your clips.
Use a program such as **tovid** to author the dvd.
Use a program such as **k3b** to burn it to disc.

All these three programs are in the Ubuntu repo.
I'm sure that there will be more suggestions to follow.
:D

---

### Post by alegallo on 2010-02-16
Sure, ron999, here is another one ;)

- Kino, capture and basic editing (it is NOT a KDE app, even if it's a K- one :D );
- DVDStyler, authoring, lots of configuration options available, produces a .iso image;
- any burner to burn the disc (Brasero, k3b, or whatever you like).

The above are all in the repos.

If you need some deeper editing you can use kdenlive (this IS a kde app), pitivi or openshot, or you can get even more with Cinelerra.
Authoring can be done also with ManDVD, DVDauthorGUI and many more.

---


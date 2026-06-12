---
title: "Miscrosoft Visual C++ Runtime Library error in Starcraft II install"
date: 2011-03-15
forum: Wine
---

### Post by wonderweirdo on 2011-03-15
I've been having a hard time installing StarCraft II and I keep getting an error when it gets to about 53% installed, Microsoft Visual C++ Runtime Library.  See the screen shot.  I researched it and one of the ways I found was to install the correct environment in Winetricks, but I don't know what environment to install.
I've tried installing this game from the disk, the online installer, but the results are the same.  I'm using Wine 1.3.15 and Ubuntu 10.10.

Is there anyone who has encountered this before and knows how to fix it"?

---

### Post by face_mcgace on 2011-08-10
If you're getting runtime errors it has to do with your libraries that you have downloaded. (I had the same problem, and it seems to have fixed it so far [fingers crossed].

What I did was install wine 1.3, go into winetricks--> install app, and install vc2005express (for me it didn't install all the way but it still worked?? no clue..)

Then I installed the 2010 Windows C++ package, but I'm not sure how much that helped.

Hopefully it works for you :)

---


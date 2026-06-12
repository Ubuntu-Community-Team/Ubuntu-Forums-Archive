---
title: "How GNU/Linux beat the pants off Windows MCE"
date: 2008-02-16
forum: The Cafe
---

### Post by k2t0f12d on 2008-02-16
This story starts with a Dell Photo AIO 964 (which is really a rebranded Lexmark x7170 with absolutely *NO* GNU/Linux driver support, free software or otherwise), and a Dell8400 P4 3.2ghz 1gb core running Windows MCE.  Since a family member had fried my Brother MFC, I was using their computer [the Dell] to which I would connect using Samba and use their 964 AIO for scanning.

I was taxing his system to the limit when scanning in 25-36 square inch clips @ 1200dpi.  The files created would be approximately 250-300mb.  Unfortunately, it requires a great deal more core to manipulate that size image, which proved to be possible only with coaxing.  The first thing that went wrong was Window's complaints insisting there was not enough RAM to store the clip.  I managed, in some instances, by dividing it up in clever ways so I could reassemble the image in GIMP.  The scan would go through, meanwhile deadlocking every single other function and application running on the Dell while scanning.  Once jumping that hurdle, the next debacle was the bizarre need to shut down Photoshop to clear the memory it had been using each and everytime I wanted to perform a new capture, regardless of the fact the image I scanned had already shipped over to my PC, and should have no longer been in memory.  Eventually the hassle became more then I could bear, and I resolved to put off my imaging work and  wait until I got a scanner that worked with GNU/Linux.

Now I have a Hewlett/Packard PhotoSmart AIO C7280.  It works with full functionality after installing the hplip drivers with the installer from SourceForge.  I know the Debian repositories have a package for it, but the latest from SourceForge *does* work better, and automatically sets up your printing, fax, and scanner with supreme ease after package installation.

Tonight, I have scanned over 56 square inches, in one go, with xsane through GIMP (thats over twice what Windows would let me do w/o RAM complaints), for a final image size of 9068x10932 pixels, and a max swap usage at 1274mb of 2055mb.  I flipped the image and saved, then scanned another of the same size.  The machine Im using tonight is a P4 2.4ghz and 1gb core running Debian testing. Working with such incredibly large images is unsurprisingly pretty sluggish, the only difference being that with GNU/Linux it is *possible*. My applications also remain responsive during the scan, and are only a little sluggish when performing transforms, and I don't have to close applications to clear memory usage, *and* I can do it over and over with image sizes twice that which Windows would permit on more powerful equipment.

Windows unequivocally blows.

:guitar:

---

### Post by Xavieran on 2008-02-16
Awesome!

I too must say that linux easily beats the pants off of windows...
For example it would be way too easy to simply create a simple "failsafe x session" that only loads a browser at startup for an internet cafe or the like...

But in windows one must purchase (or write) a whole program to do that...:)

---


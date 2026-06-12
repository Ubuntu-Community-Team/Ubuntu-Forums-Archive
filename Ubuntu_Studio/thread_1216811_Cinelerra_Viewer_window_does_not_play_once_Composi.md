---
title: "Cinelerra Viewer window does not play once Compositor is played"
date: 2009-07-18
forum: Ubuntu Studio
---

### Post by Cyclops_ on 2009-07-18
Hey, all,

I am editing some video in Cinelerra, and here is the issue I am running into...

I can load files into the Viewer Window, and play them great, and go forward and backward, and set start and end points, and clip, and splice, etc....   BUT, as soon as I play the main window ( the compisitor ), the Viewer window does not play video anymore.  It will play the audio just fine, but the video is paused... at least until I pause the Viewer window, and then i get the thumbnail of the video of where I paused it at.

Any help on figuring this out would be great!

Thanks in advance!

---

### Post by geist3 on 2009-08-16
I have the same issue, AMD64 with 64bit Ubuntu
Using MPG files
didn't find anything on [http://bugs.cinelerra.org](http://bugs.cinelerra.org)

---

### Post by ptimlick on 2011-01-09
Settings->Preferences->Playback->Playeveryframe=false worked for me on 9.04 Koala 32 bit.

When I installed Lucid 10.04, 64 bit (with 4GB ram) it the cinelerra "viewer window" was again non-functional.

Based upon performance section in [http://heroinewarrior.com/cinelerra/cinelerra.html#IMPROVING-PERFORMANCE](http://heroinewarrior.com/cinelerra/cinelerra.html#IMPROVING-PERFORMANCE) , I investigated turning off swap.

I came across [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and it recommended

sudo sysctl vm.swappiness=10

I tried it, it worked, and I am pressing on with other issues..

Hope it works for you too.

Good luck

---

### Post by amirstep on 2011-02-06
I tried this and it solved the problem:

Under Settings > Preferences > Playback -- at the bottom of Video Out, change to X11-OpenGL.  Not sure why this worked, but it did.

-a

---

